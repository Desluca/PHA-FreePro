# PHA-FreePro

**Software open source per Process Hazard Analysis (PHA), HAZOP e LOPA.**

PHA-FreePro serve a condurre, documentare e seguire nel tempo gli studi di sicurezza di processo negli impianti industriali (chimica, oil & gas, farmaceutica, energia). Offre le funzionalità che i professionisti si aspettano dagli strumenti PHA commerciali: worksheet HAZOP, matrice di rischio, LOPA collegata con calcolo del SIL, librerie riutilizzabili, gestione delle raccomandazioni, report Word/Excel/PDF. È gratuito, ha un formato dati aperto e gira anche offline.

> **Stato: progettazione (Fase 0).** Il codice non esiste ancora. Il repository contiene la ricerca, le specifiche funzionali e il piano di progetto. Vedi il [PLANNER](docs/PLANNER.md).

> **Avviso.** PHA-FreePro è un progetto indipendente: non è affiliato, approvato o sponsorizzato da Sphera Solutions. "PHA-Pro" è un marchio di Sphera ed è citato solo come prodotto di riferimento per il confronto funzionale. Nessun codice, contenuto, testo o elemento grafico di prodotti commerciali viene riutilizzato.

## Funzionalità previste

| Area | Funzionalità |
|---|---|
| **Interfaccia** | Workspace con studi aperti e librerie attive, fogli a schede, procedura guidata per il nuovo studio |
| **Metodologie** | HAZOP (IEC 61882), What-If, Checklist, LOPA (CCPS), SIL (IEC 61511); poi FMEA, HAZID, CHAZOP, HACCP, DHA, SIMOPS, Security, bow-tie |
| **Worksheet** | Griglia gerarchica Nodo → Deviazione → Causa → Conseguenza → Salvaguardie; tutto da tastiera; AutoType; Copy From; mirroring dati tra fogli; liste strutturate; viste personalizzabili; note, allegati e statistiche di cella |
| **Rischio** | Più risk system configurabili (3×3 … 7×7), rischio prima e dopo la riduzione, heat map ibrida |
| **LOPA / SIL** | Scenari collegati all'HAZOP, eventi iniziatori, IPL con PFD, frequenza mitigata; SIL da LOPA, Risk Graph o Safety Layer Matrix |
| **Disegni** | P&ID in PDF con evidenziazione dei nodi; diagramma collegato disegnato nel programma |
| **Qualità dei dati** | Analisi (statistiche e grafici) e Controllo dati (completezza, regole, eccezioni) |
| **Team** | Membri, sessioni, registro presenze |
| **Librerie** | Guideword, parametri, cause, salvaguardie, IPL, checklist (obiettivo ≥ 2.500 voci) e knowledge base aziendale |
| **Raccomandazioni** | Responsabili, scadenze, workflow, evidenze di chiusura, notifiche, dashboard |
| **Report** | DOCX, XLSX, PDF, HTML, CSV; template personalizzabili; filtri |
| **Template** | Metodologie definite come template JSON, modificabili con un designer visuale |
| **Governance** | Audit trail per campo, approvazione bozza e release firmate, Change Log, Revision Chain, revalidation, protezione dello studio |
| **Sicurezza** | Ruoli e permessi, LDAP/AD, OIDC, 2FA |
| **Deployment** | App desktop (Windows/macOS/Linux) e server on-premise (Docker) |
| **Lingue** | Italiano e inglese, poi DE/FR/ES/PT/JA/ZH/KO e dati right-to-left |

## Documentazione

| Documento | Contenuto |
|---|---|
| [00 — Ricerca e fonti](docs/00-ricerca-fonti.md) | Cosa sappiamo del prodotto di riferimento, con fonti e livello di affidabilità |
| [Relazione dettagliata sul software di riferimento](docs/Documentazione_PHA-Pro_completa.md) | Interfaccia, schede, flussi, configurazione, release e troubleshooting del prodotto di riferimento, con fonti S1–S13 |
| [01 — Panoramica](docs/01-panoramica.md) | Scopo, utenti, ciclo di vita di uno studio, mappa dei moduli, requisiti non funzionali |
| [02 — Metodologie](docs/02-metodologie.md) | HAZOP, What-If, Checklist, FMEA, HAZID, matrice di rischio, LOPA/SIL, bow-tie |
| [03 — Moduli](docs/03-moduli.md) | Specifica di ogni modulo (M0–M20) con criteri di accettazione |
| [04 — Modello dati](docs/04-modello-dati.md) | Diagramma ER, entità, esempio di template, formule |
| [05 — Architettura](docs/05-architettura.md) | Stack, struttura del repository, sync offline, formato file, API, sicurezza |
| [06 — Glossario](docs/06-glossario.md) | Termini di process safety |
| [PLANNER](docs/PLANNER.md) | Roadmap, milestone, backlog con stime, decisioni, rischi |

## Roadmap in breve

| Milestone | Obiettivo | Periodo indicativo |
|---|---|---|
| M0 | Motore template + griglia prototipo | dicembre 2026 |
| M1 — v0.1 | HAZOP completo desktop, matrice, librerie, controllo dati, export Word/Excel | maggio 2027 |
| M2 — v0.5 | LOPA/SIL, P&ID e diagramma collegato, Analisi, What-If, Checklist, report completi | settembre 2027 |
| M3 — v1.0 | Server multiutente, offline sync, Recommendations Manager, release e revalidation | gennaio 2028 |
| M4 — v1.5 | Template designer, FMEA e altri metodi, bow-tie, API, altre lingue | aprile 2028 |

Date calcolate per 1 sviluppatore; con 2–3 sviluppatori si accorciano di circa il 40%.

## Stack previsto

TypeScript · React · TanStack Table · PDF.js · Fastify · Drizzle ORM · PostgreSQL / SQLite · Tauri. Dettagli e motivazioni in [05-architettura.md](docs/05-architettura.md) (decisione D-01, ancora da confermare).

## Come contribuire

Il progetto è all'inizio. Contributi utili ora:
- **Esperti di process safety**: revisione delle specifiche ([02](docs/02-metodologie.md), [03](docs/03-moduli.md)) e contenuti di libreria (cause, salvaguardie, voci di checklist) da fonti di pubblico dominio, citando sempre la fonte.
- **Sviluppatori**: task della Fase 0 nel [PLANNER](docs/PLANNER.md).

Non inviare materiale proprietario (manuali, librerie, schermate o file di software commerciali).

## Disclaimer

PHA-FreePro è uno strumento di supporto. I risultati di una PHA dipendono dalla competenza del team e dalla qualità dei dati inseriti. I calcoli LOPA/SIL vanno verificati da personale qualificato prima di essere usati per decisioni di sicurezza.

## Licenza

[MIT](LICENSE) © 2026 Luca Gruppi
