# 01 — Panoramica del programma

## Che cos'è PHA-FreePro

PHA-FreePro è un software open source (licenza MIT) per condurre, documentare e seguire nel tempo le **Process Hazard Analysis (PHA)** negli impianti di processo: raffinerie, chimica, farmaceutica, oil & gas, energia, alimentare.

Riproduce le funzionalità che i professionisti si aspettano da uno strumento PHA/HAZOP commerciale (vedi [00-ricerca-fonti.md](00-ricerca-fonti.md)). Ha due differenze di fondo:

1. **Aperto**: formato dati documentato, API REST, nessun lock-in.
2. **Configurabile**: le metodologie sono **template** su un motore generico, non codice cablato. HAZOP, What-If, Checklist, FMEA e LOPA sono template forniti di serie; l'utente può modificarli o crearne di nuovi.

## A chi serve

| Ruolo | Cosa fa nel programma |
|---|---|
| **Facilitatore / Chairman** | Crea lo studio, guida le sessioni, compila i fogli in tempo reale, proietta lo schermo al team |
| **Scriba (Scribe)** | Inserisce i dati durante la riunione; usa molto AutoType e le librerie |
| **Membro del team** (processo, strumentazione, sicurezza, operazioni, manutenzione) | Consulta, commenta, firma la partecipazione alle sessioni |
| **Responsabile azione** (Action owner) | Riceve le raccomandazioni, aggiorna lo stato, carica le evidenze di chiusura |
| **Process Safety Manager** | Controlla il portafoglio di studi, il rischio residuo, le azioni scadute; approva le chiusure |
| **Amministratore** | Gestisce utenti, ruoli, template, librerie, matrici di rischio aziendali, LDAP/SSO |
| **Auditor / Ente esterno** | Accesso in sola lettura a report filtrati e alla cronologia delle modifiche |

## Il ciclo di vita di uno studio

```
 ┌────────────┐   ┌─────────────┐   ┌────────────┐   ┌─────────────┐   ┌───────────┐   ┌──────────┐
 │ 1. Setup   │──▶│ 2. Prepara- │──▶│ 3. Sessioni│──▶│ 4. Revisione│──▶│ 5. Rilascio│──▶│ 6. Follow│
 │   studio   │   │   zione     │   │   di analisi│   │   & LOPA    │   │  & report │   │  -up azioni│
 └────────────┘   └─────────────┘   └────────────┘   └─────────────┘   └───────────┘   └──────────┘
```

1. **Setup**: scelta del template (es. "HAZOP + LOPA, matrice 5×5 aziendale"), dati generali dello studio (impianto, unità, scopo, confini, revisione), team.
2. **Preparazione**: caricamento dei P&ID e dei documenti di riferimento; definizione dei **nodi** e dell'intento progettuale; selezione delle **deviazioni** applicabili da libreria (guideword × parametro).
3. **Sessioni**: per ogni nodo e deviazione il team individua **cause → conseguenze → salvaguardie esistenti**, assegna **severità e probabilità**, calcola il **rischio**, emette **raccomandazioni**. Il programma registra data, durata e presenti di ogni sessione.
4. **Revisione & LOPA**: gli scenari ad alto rischio vengono trasferiti automaticamente nel foglio LOPA (scenari collegati, non copiati); si identificano gli IPL, si calcola la frequenza mitigata, si determina il **SIL** richiesto.
5. **Rilascio**: lo studio viene "congelato" in una **release** (revisione A, B, 0…) con firma; si generano i report (Word/Excel/PDF/HTML).
6. **Follow-up**: le raccomandazioni vivono nel **Recommendations Manager** con responsabile, scadenza, stato, evidenze e verifica di chiusura, anche dopo la chiusura dello studio. Lo studio si rivaluta ogni 5 anni (revalidation, OSHA PSM) partendo dalla release precedente.

## Mappa dei moduli

| # | Modulo | Descrizione breve | Dettaglio |
|---|---|---|---|
| M1 | Gestione progetti/studi | Elenco studi, apertura, duplicazione, archiviazione, revalidation | [03](03-moduli.md#m1) |
| M2 | Dati dello studio | Informazioni generali, scopo, documenti, assunzioni | [03](03-moduli.md#m2) |
| M3 | Team e sessioni | Membri, competenze, presenze per sessione, durata | [03](03-moduli.md#m3) |
| M4 | Disegni (P&ID) | Caricamento PDF/immagini, evidenziazione nodi, link bidirezionale | [03](03-moduli.md#m4) |
| M5 | Worksheet engine | Griglia gerarchica/tabellare, AutoType, Copy From, mirroring, liste strutturate | [03](03-moduli.md#m5) |
| M6 | Template HAZOP | Nodi, deviazioni, cause, conseguenze, salvaguardie, rischio | [02](02-metodologie.md#hazop) |
| M7 | Altri template | What-If, Checklist, FMEA, HAZID, PHA preliminare | [02](02-metodologie.md) |
| M8 | Matrice di rischio | Criticality matrix configurabile, rischio iniziale/residuo | [03](03-moduli.md#m8) |
| M9 | LOPA e SIL | Scenari collegati, IPL, PFD, frequenze, gap, SIL target | [02](02-metodologie.md#lopa) |
| M10 | Librerie / Knowledge base | Guideword, parametri, cause, salvaguardie, checklist (≥2.500 voci obiettivo) | [03](03-moduli.md#m10) |
| M11 | Recommendations Manager | Azioni, responsabili, scadenze, workflow, evidenze, dashboard | [03](03-moduli.md#m11) |
| M12 | Report ed export | Report predefiniti e personalizzati, filtri, Word/Excel/PDF/HTML | [03](03-moduli.md#m12) |
| M13 | Template designer | Editor di gerarchia, fogli, colonne, liste, matrici | [03](03-moduli.md#m13) |
| M14 | Release e change tracking | Revisioni, audit trail campo per campo, confronto release | [03](03-moduli.md#m14) |
| M15 | Sicurezza e amministrazione | Utenti, ruoli, permessi per studio, LDAP/OIDC, 2FA | [03](03-moduli.md#m15) |
| M16 | Internazionalizzazione | UI multilingua, dati RTL, librerie multilingua | [03](03-moduli.md#m16) |
| M17 | Bow-tie (opzionale) | Diagramma bow-tie generato dagli scenari | [02](02-metodologie.md#bowtie) |
| M18 | Import / API | Import Excel, API REST, interscambio JSON | [03](03-moduli.md#m18) |

## Requisiti non funzionali chiave

- **Funziona offline** durante le sessioni (sale riunioni in impianto spesso senza rete), con sincronizzazione successiva.
- **Velocità di inserimento**: tutto da tastiera; uno scriba esperto non deve mai toccare il mouse.
- **Proiettabile**: modalità presentazione con caratteri grandi e alto contrasto.
- **Tracciabilità**: ogni modifica ha chi/quando/cosa; le release sono immutabili.
- **Scalabilità**: studi con 50+ nodi e 5.000+ righe restano fluidi.
- **Accessibilità**: WCAG 2.1 AA per l'interfaccia web.
