# 00 — Ricerca e fonti

Questo documento raccoglie **cosa sappiamo del prodotto di riferimento** (Sphera PHA-Pro®) e **da dove viene** ogni informazione. Serve a distinguere ciò che è confermato da fonti pubbliche da ciò che deriviamo dalla pratica di settore (norme HAZOP/LOPA) o che va ancora verificato.

> **Nota legale.** PHA-FreePro è una **reimplementazione indipendente** delle *funzionalità* tipiche di un software PHA/HAZOP. Non usiamo codice, file, librerie di contenuti, testi della guida, grafica, icone o marchi di Sphera. "PHA-Pro" è un marchio registrato di Sphera Solutions; è citato solo a scopo di confronto. Vedi anche [PLANNER.md](PLANNER.md), rischio R-01 (nome del progetto).

Data ricerca: 10 novembre 2026.

## Legenda affidabilità

| Sigla | Significato |
|---|---|
| **[F]** | Confermato da fonte ufficiale Sphera (pagina prodotto o brochure) |
| **[G]** | Da estratti della *PHA-Pro User Guide 8.3.4* (apr. 2013) indicizzati da motori di ricerca — testo completo non accessibile |
| **[D]** | Dedotto dalla pratica di settore / norme (IEC 61882, CCPS LOPA, IEC 61511) — è come lavora qualunque tool HAZOP |
| **[V]** | Da verificare (es. guardando i video demo dopo registrazione) |

## 1. Prodotto di riferimento in sintesi

- Software desktop/enterprise per **Process Hazard Analysis**, nato da Dyadem, poi IHS, oggi Sphera. Versione 8.x documentata (8.3.4 nel 2013, 8.21 citata in titoli video). [F][G]
- Settori: oil & gas, chimico, farmaceutico. [F]
- Metodologie esplicitamente citate: **HAZOP, What-If, LOPA**, con **template HAZOP e LOPA collegati**. [F]
- Prodotto gemello: **FMEA-Pro** (stessa piattaforma, metodologia FMEA). [F]
- Lingue: inglese, francese, tedesco, spagnolo, portoghese, giapponese, cinese semplificato, coreano; inserimento dati **right-to-left**. [F]
- Deployment: on-premise e cloud citati da fonti terze; **nessuna API pubblica**, **nessuna app mobile** (secondo softwarefinder, giugno 2026). [F terzi]

## 2. Funzionalità confermate dalla brochure ufficiale (2021) [F]

**Conformità normativa supportata:** OSHA 1910.119 PSM, EPA 40 CFR Part 68 RMP, Direttiva Seveso, CCPS LOPA, IEC 61882, IEC 61511 / IEC 61508 / ANSI/ISA S84.00.01, ISO 31000, AS/NZS 4360, CSA Z1000.

**Capacità:**
- Collegamento dinamico **diagrammi ↔ fogli di lavoro** (P&ID collegati ai nodi).
- Report professionali esportabili in **HTML, MS Word, MS Excel**; report di stampa preformattati; report filtrati.
- **AutoType** e **Copy** avanzati (riuso testo già inserito).
- **Release Management** (gestione rilasci/versioni dello studio).
- **Criticality Matrix** (matrice di rischio).
- **Recommendations Manager** (gestione e tracking raccomandazioni/azioni).
- **Knowledge base**: librerie precompilate con **oltre 2.500 voci di checklist**; riuso di studi precedenti per costruire librerie aziendali.
- **Template personalizzabili**: modifica di worksheet e form, creazione di nuovi template per altre metodologie.
- **Dependency Matrix**: fogli a matrice per nuove tecniche di valutazione.
- **Conditional Data Mirroring**: replica automatica di dati tra fogli, senza reinserimento.
- **Structured Lists**: strutture ad albero ad hoc tramite indentazione delle righe.
- **Enhanced Change Tracking**: tracciamento modifiche per l'integrità del change management.
- **Sicurezza**: doppia autenticazione, Windows Authentication, LDAP per diritti di accesso; document control; strumenti di audit.

## 3. Elementi dalla User Guide 8.3.4 (estratti) [G]

- Il file di progetto ha **Project Settings** con una sezione **Hierarchy** che definisce le relazioni gerarchiche fra tipi di dati (es. Nodo → Deviazione → Causa → Conseguenza…).
- **Keyword**: ogni livello della gerarchia ha una keyword; colonne con la stessa keyword condividono AutoType / Copy From anche fra fogli diversi.
- **Sheets** indipendenti dalla gerarchia: i fogli sono *viste* sulla gerarchia. Una matrice richiede un foglio dedicato creato nella sezione Sheets.
- **Lists**: tipi di lista per aggiungere righe (la lista "a righe" standard).
- Guida di ~520 pagine: il prodotto è fortemente configurabile (il motore è generico, le metodologie sono template).

## 4. Video e demo

| Risorsa | Contenuto | Stato |
|---|---|---|
| [Full PHA-Pro Demo Series](https://sphera.com/resources/video/full-pha-pro-demo-series/) (Sphera, ott. 2021) | 5 parti: funzioni amministrative; worksheet HAZOP e raccomandazioni; template LOPA; reporting e analytics | Richiede registrazione [V] |
| [PHA-Pro HAZOP to BowTieXP v1.1](https://www.youtube.com/watch?v=GgKkBpjc5jo) (YouTube) | Migrazione dati HAZOP verso un tool bow-tie esterno | Solo titolo letto |
| [Sphera-PHA-Pro-Intro](https://vimeo.com/185997264) (Vimeo) | Introduzione al prodotto | Bloccato da verifica anti-bot [V] |
| Canale YouTube Sphera | Webinar vari | Non analizzato [V] |

**Conclusione sul bow-tie:** PHA-Pro non sembra avere un modulo bow-tie nativo; esiste un'esportazione verso tool bow-tie di terzi. Per noi è una funzione *opzionale* di fase avanzata.

**Azione aperta (owner: team):** registrarsi alla demo series e annotare in questo file, per ogni video, schermate/flussi osservati (senza copiare grafica). Vedi task `RES-02` nel planner.

## 4-bis. Relazione dettagliata sul software (aggiunta il 10 nov 2026)

Il file [Documentazione_PHA-Pro_completa.md](Documentazione_PHA-Pro_completa.md) è una **relazione funzionale dettagliata** del prodotto di riferimento, nella linea desktop PHA-Pro 8.x. Ogni affermazione vi è etichettata con il livello di evidenza e le fonti S1–S13. Aggiunge informazioni che le pagine Sphera non riportano. **È la fonte primaria per i flussi e la UI**; i documenti 01–05 sono stati allineati di conseguenza.

Nuovi elementi emersi (rimandi alle sezioni della relazione):

| Elemento | Sezione relazione | Recepito in |
|---|---|---|
| Finestra principale: menu, toolbar, pannello **Workspace** (Open Documents, Active Libraries), fogli a schede | §3 | [03 · M0](03-moduli.md#m0) |
| Schede tipiche: Administration, List "Nodes", List "Deviations", Develop HAZOP Worksheet, Manage Recommendations, Reports, Analyze, Settings, Data Check | §3.3 | [03 · M0](03-moduli.md#m0) |
| **New File Wizard** e campi Facility (Company, Business Unit, Facility, Project ID, Project Name, durata) | §4 | M1, M2 |
| Tipo di nodo (es. Heat Exchanger), riuso di nodi da studi precedenti | §5.1 | M6 |
| Categorie di conseguenza (es. persone, ambiente, asset, produzione), rischio **before/after risk reduction** | §6, §6.1 | M6, M8 |
| Personalizzazione dei fogli da parte dell'utente: rinominare, nascondere, trascinare colonne, formati, breakdown, filtri validi anche per la stampa | §6.2 | M5 |
| Più matrici di rischio, collegate a un livello della gerarchia; **heat map ibrida** a più livelli | §9 | M8 |
| **Linked Diagram**: schema a blocchi disegnato nel programma, con i nodi trascinati sull'area di disegno (diverso dall'evidenziazione sui P&ID) | §10 | M4 |
| Altri metodi: SIL con **Risk Graph** e **Safety Layer Matrix**, HAZID, CHAZOP, HACCP, Dust Hazard Analysis, SIMOPS, Security Assessment | §11 | [02](02-metodologie.md) |
| Report: Print Preview, **Report Collection**, intestazioni e piè di pagina dinamici, filtri, export XML | §12 | M12 |
| **Analyze** (statistiche e grafici) e **Data Check** (completezza e regole) | §13 | [03 · M19, M20](03-moduli.md#m19) |
| Settings: Hierarchy, Grid/Breakdown, Risk Systems, Codes and Categories, Data Dictionary, Forms, Charts/Formulas | §14 | M13 |
| Release Management: Draft → *Approve this Draft* (A.0), **Change Log**, **Revision Chain**, avviso se si modifica una release approvata | §15.1 | M14 |
| **Revalidation History** e marker di revalidation per cella | §15.2, §16 | M14, M5 |
| Tools › **Protection** (tre modalità, non dettagliate) | §15.3 | M15 |
| Note di cella, allegati (graffetta), statistiche per colonna (max, min, somma) | §16 | M5 |

Fonti nuove citate dalla relazione: brochure Sphera 2025, *PHA-Pro 8 End-User Exercises* (non ufficiale), report pubblici di progetto che mostrano la UI (DEKRA/IOCL 2014, H2Tools), guida ProcessEng 2019, UNECE 2024, EnVizTec. Video indicato: [YouTube jfCmCVNGgaU dal minuto 01:21](https://www.youtube.com/watch?v=jfCmCVNGgaU&t=81s), non ancora trascritto (vedi `RES-02`).

> I contenuti di esempio della relazione (aziende, scenari, codici di categoria) sono **illustrativi**: non vanno copiati nelle librerie di serie.

## 5. Concorrenti utili come riferimento funzionale

- **Kenexis Open-PHA** — tool HAZOP/LOPA web; manuale utente pubblico; stesso dato mostrato come HAZOP, LOPA o bow-tie.
- **Primatech PHAWorks RA** — PHA/LOPA, genera bow-tie dagli scenari.
- **BowTieXP** — bow-tie dedicato.

## 6. Elenco fonti

- https://sphera.com/process-hazard-analysis-pha-pro-hazop
- https://sphera.com/solutions/process-safety-management/advanced-risk-assessment-software-and-services/process-hazard-analysis-pha-pro-hazop/
- https://sphera.com/pha-pro/
- https://sphera.com/wp-content/uploads/2024/09/PHA-Pro-Brochure-Updated.pdf (brochure 2021)
- https://sphera.com/resources/video/full-pha-pro-demo-series/
- https://softwarefinder.com/manufacturing-software/pha-pro
- https://www.scribd.com/doc/310948754/PHA-Pro-User-Guide-8-3-4 (solo metadati)
- https://www.youtube.com/watch?v=GgKkBpjc5jo
- https://vimeo.com/185997264
- https://www.kenexis.com/software/openpha/
- https://www.aiche.org/resources/publications/cep/2019/february/enhancing-phas-power-bowties
