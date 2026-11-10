# 05 — Architettura tecnica (proposta)

> Stato: **proposta da confermare** (decisione `D-01` nel [PLANNER](PLANNER.md)). Le scelte sono motivate sotto, così si possono rivedere.

## Obiettivi che guidano le scelte

1. Lavoro **offline** in sala HAZOP e sincronizzazione successiva.
2. Griglia molto veloce con migliaia di righe.
3. Calcoli (matrice, LOPA, validazioni) **identici** su client e server.
4. Installabile **on-premise** (molte aziende di processo non vogliono il cloud) e anche **desktop singolo utente**.
5. Tutto open source con licenze permissive (MIT/Apache/BSD).

## Stack proposto

| Strato | Tecnologia | Motivo |
|---|---|---|
| Linguaggio | **TypeScript** end-to-end | Stesso motore di template/formule/validazione su client e server |
| Monorepo | pnpm workspaces + Turborepo | Pacchetti condivisi |
| Frontend | **React 19 + Vite** | Ecosistema maturo |
| Griglia | **TanStack Table + TanStack Virtual** (MIT) con editor celle custom | Virtualizzazione righe/colonne, celle fuse, controllo totale della tastiera |
| UI kit | Radix UI + Tailwind CSS | Accessibile, temabile |
| Disegni | **PDF.js** + overlay SVG/Konva per le evidenziazioni | Rendering PDF in browser |
| Stato/offline | IndexedDB (Dexie) + coda di operazioni; sincronizzazione con versioni per record | Funziona senza rete |
| Backend | **Node.js 22 + Fastify** | Leggero, veloce, OpenAPI integrato |
| ORM / DB | **Drizzle ORM + PostgreSQL 16** (server); **SQLite** (desktop) | Stesso schema su entrambi; JSONB per i valori di cella |
| Ricerca | Full-text PostgreSQL (tsvector) / FTS5 su SQLite | Nessun servizio extra |
| File | Filesystem locale o S3-compatibile (MinIO) | Disegni e allegati |
| Auth | Sessioni + TOTP; **openid-client** (OIDC), **ldapts** (LDAP), SAML via proxy | M15 |
| Report | **docx** (DOCX), **ExcelJS** (XLSX), HTML → PDF via **Playwright/Chromium** | Formati richiesti |
| Desktop | **Tauri 2** con backend embedded e SQLite | Installer leggero per Windows/macOS/Linux |
| Email | Nodemailer (SMTP) | Notifiche azioni |
| Test | Vitest (unit), Playwright (E2E) | |
| Distribuzione | Docker Compose (server), MSI/DMG/AppImage (desktop) | |

## Struttura del repository (target)

```
PHA-FreePro/
├─ apps/
│  ├─ web/            # React SPA
│  ├─ server/         # Fastify API
│  └─ desktop/        # Tauri shell
├─ packages/
│  ├─ core/           # modello dati, motore template, formule, validazioni (puro TS, nessuna dipendenza UI)
│  ├─ risk/           # matrice, LOPA, SIL, RPN
│  ├─ grid/           # componente worksheet
│  ├─ reports/        # generatori DOCX/XLSX/PDF/HTML
│  ├─ db/             # schema Drizzle + migrazioni
│  └─ i18n/           # traduzioni
├─ templates/         # template di serie (hazop, hazop-lopa, whatif, checklist, fmea, hazid) in JSON
├─ libraries/         # librerie di serie (guideword, cause, checklist…) in JSON/CSV con fonte
├─ docs/
└─ README.md
```

## Architettura logica

```
┌──────────────────────── Client (browser o Tauri) ────────────────────────┐
│  UI React ── Worksheet grid ── Visualizzatore P&ID ── Report preview      │
│        │                                                                  │
│  @pha/core (template engine, formule, validazione, LOPA)                 │
│        │                                                                  │
│  Store locale (IndexedDB/SQLite) ── Coda operazioni ── Sync client        │
└────────┼──────────────────────────────────────────────────────────────────┘
         │ HTTPS: REST + WebSocket (presenza, aggiornamenti live)
┌────────▼──────────────────────── Server ──────────────────────────────────┐
│  Fastify: auth · studi · righe · sync · raccomandazioni · librerie · report│
│  @pha/core (stessa validazione lato server)                              │
│  Job queue (pg-boss): report pesanti, e-mail, scadenze                    │
│  PostgreSQL ── Object storage (disegni, allegati, release)               │
└───────────────────────────────────────────────────────────────────────────┘
```

## Sincronizzazione e concorrenza

- Ogni modifica è un'**operazione** (`createRecord`, `setCell`, `moveRecord`, `deleteRecord`…) con id, autore e versione base.
- Il client applica subito in locale (UI reattiva) e invia al server; il server valida, assegna un numero di sequenza e la trasmette agli altri client.
- Conflitti: **last-writer-wins per cella** con notifica e storico (in HAZOP di solito scrive una persona sola — lo scriba); lock opzionale "sessione attiva" che rende gli altri in sola lettura.
- Il log delle operazioni alimenta direttamente l'**audit trail** (M14).

<a id="formato-file"></a>
## Formato file `.phaf` (PHA FreePro File)

Archivio ZIP con:
```
manifest.json      # versione formato, app, hash
study.json         # studio, team, sessioni, record, celle, link, raccomandazioni
template.json      # versione del template usata
matrix.json        # matrice di rischio
drawings/…         # PDF/immagini + markups.json
attachments/…
releases/…         # snapshot opzionali
```
Specifica pubblicata con JSON Schema in `docs/format/` (fase 2).

## API REST (estratto)

| Metodo | Endpoint | Descrizione |
|---|---|---|
| GET | `/api/studies?plant=&status=` | Elenco studi |
| POST | `/api/studies` | Crea da template / copia / revalidation |
| GET | `/api/studies/{id}/records?level=&sheet=` | Righe di un foglio |
| POST | `/api/studies/{id}/ops` | Batch di operazioni (sync) |
| GET | `/api/studies/{id}/lopa` | Scenari LOPA calcolati |
| POST | `/api/studies/{id}/releases` | Crea release firmata |
| GET | `/api/recommendations?owner=me&status=open` | Azioni |
| PATCH | `/api/recommendations/{id}` | Transizione di stato |
| POST | `/api/studies/{id}/reports` | Genera report (asincrono) |
| GET/POST | `/api/libraries/{type}` | Librerie |

## Sicurezza

- OWASP ASVS livello 2 come riferimento; password Argon2id; CSRF su sessioni cookie; rate limit su login.
- Autorizzazione verificata lato server su ogni operazione (ruolo × studio).
- Export e download registrati nel log di sicurezza.
- Hash SHA-256 delle release; firma elettronica = ri-autenticazione + motivo.
- Backup: `pg_dump` + storage; procedura documentata.

## Prestazioni (budget)

| Operazione | Budget |
|---|---|
| Apertura studio 5.000 righe | < 2 s |
| Scroll griglia | 60 fps |
| AutoType | < 100 ms |
| Calcolo LOPA di tutti gli scenari | < 200 ms |
| Report completo DOCX | < 30 s |
