# 03 — Moduli in dettaglio

Ogni modulo è descritto con: **scopo**, **funzioni**, **interfaccia**, **regole** e **criteri di accettazione** (usati anche come Definition of Done nel [PLANNER](PLANNER.md)).

---

<a id="m1"></a>
## M1 — Gestione progetti e studi

**Scopo:** punto di ingresso; elenco di tutti gli studi accessibili all'utente.

**Funzioni**
- Elenco studi con filtri (impianto, unità, metodologia, stato, data, facilitatore) e ricerca full-text.
- Nuovo studio: da template, da studio esistente (copia), o da **revalidation** (copia dell'ultima release con link alla precedente).
- Stati dello studio: `Bozza → In corso → In revisione → Rilasciato → Archiviato`.
- Struttura organizzativa: **Organizzazione → Sito → Impianto → Unità**, usata per permessi e report di portafoglio.
- Import/export dello studio come file singolo `.phaf` (vedi [05-architettura.md](05-architettura.md#formato-file)) per lavorare offline o scambiare con consulenti esterni.

**Accettazione:** creare uno studio da template HAZOP in ≤ 3 clic; duplicare uno studio di 2.000 righe in < 5 s.

---

<a id="m2"></a>
## M2 — Dati dello studio (Study Information)

Form strutturato (configurabile dal template) con: titolo, codice, impianto/unità, scopo e confini, metodologia, data inizio/fine, revisione, cliente/società di consulenza, **documenti di riferimento** (elenco con codice, revisione, link/file), **assunzioni** e **esclusioni**, criteri di rischio usati (matrice), note sul precedente studio e sugli **incidenti storici** considerati.

---

<a id="m3"></a>
## M3 — Team e sessioni

**Team:** nome, società, ruolo nello studio (Facilitatore, Scriba, Processo, Strumentista, Operazioni, HSE, Manutenzione…), qualifica/anni di esperienza, contatti. Può essere collegato a un utente del sistema o essere solo anagrafica.

**Sessioni:** data, ora inizio/fine, durata calcolata, luogo/remoto, **presenze** (matrice membri × sessioni con spunta), nodi discussi, note. Report: *attendance record* richiesto dagli audit PSM (verifica che ogni sessione abbia almeno le competenze obbligatorie presenti — regola configurabile, es. "almeno un esperto di processo e un operatore").

**Tracciamento automatico:** durante una sessione aperta, ogni riga creata o modificata viene marcata con l'ID della sessione: si sa *quando* è stato discusso ogni scenario.

---

<a id="m4"></a>
## M4 — Disegni (P&ID) e link dinamico

**Funzioni**
- Caricamento di P&ID e PFD in **PDF** (multi-pagina), PNG, JPG, SVG; metadati: numero disegno, revisione, titolo.
- Visualizzatore con zoom/pan fluido, anche su disegni A0.
- **Evidenziazione nodi**: si disegnano poligoni/polilinee colorate sul disegno; ogni colore = un nodo. Una legenda mostra nodi e colori.
- **Link bidirezionale**: clic sull'area evidenziata → apre il nodo nel worksheet; dal nodo → apre il disegno centrato sull'area.
- Marcatori per tag (es. "PSV-101") collegabili a salvaguardie/IPL.
- Export dei disegni marcati (PDF con evidenziazioni) da allegare al report.
- Le revisioni dei disegni sono conservate; avviso se un nodo punta a una revisione superata.

**Accettazione:** PDF A0 a 20 pagine visualizzato e navigabile in < 2 s per pagina.

---

<a id="m5"></a>
## M5 — Worksheet engine (cuore del programma)

Il motore che rende ogni metodologia un semplice template.

### Viste
- **Vista tabellare (spreadsheet)**: le celle dei livelli superiori si fondono verticalmente sulle righe figlie (come un report HAZOP classico).
- **Vista gerarchica/albero**: pannello laterale con l'albero Nodo → Deviazione → Causa… per navigare e riordinare con drag & drop.
- **Vista form**: un singolo record a schermo intero, utile per testi lunghi.
- **Modalità presentazione**: font grande, colonne selezionate, per il proiettore.

### Editing
- Navigazione completa da tastiera: `Tab`/`Shift+Tab` tra colonne, `Invio` nuova riga figlia, `Ctrl+Invio` nuova riga sorella, `Ctrl+↑/↓` sposta riga, `Alt+→/←` indenta/disindenta (liste strutturate).
- **AutoType**: mentre si digita, suggerimenti da (a) voci già usate nello studio nella stessa *keyword*, (b) librerie, (c) altri studi dell'organizzazione (opzionale). Ricerca fuzzy, completamento con `Tab`.
- **Copy From**: finestra per pescare righe (con o senza figli) da questo o altri studi/librerie.
- **Link / Mirroring condizionale**: una cella o un sotto-albero può essere un *link* a un'altra posizione; le modifiche si propagano. Regole condizionali (es. "mirror nel foglio LOPA se R ≥ 15").
- **Liste strutturate**: righe con indentazione libera per breakdown ad hoc (es. salvaguardie raggruppate per tipo).
- Colonne calcolate (formule semplici: lookup matrice, prodotto, somma, concatenazione, condizionale).
- Annulla/ripeti illimitato per sessione; trova e sostituisci; controllo ortografico multilingua.
- Rich text leggero nelle celle (grassetto, elenchi), allegati per riga.
- Filtri e ordinamenti per colonna; "mostra solo righe con rischio ≥ X"; "mostra righe senza raccomandazioni ma rischio alto".
- Rinumerazione automatica (1, 1.1, 1.1.1) e numerazione stabile per i riferimenti.

### Validazione
Regole configurabili per foglio: campi obbligatori, valori ammessi, coerenza (es. R residuo ≤ R iniziale), warning visivi in cella e pannello "Problemi" con link alle righe.

**Accettazione:** 5.000 righe scorrevoli a 60 fps; inserimento di una riga completa HAZOP solo da tastiera; AutoType risponde in < 100 ms.

---

<a id="m8"></a>
## M8 — Matrice di rischio

Vedi [02-metodologie.md §6](02-metodologie.md#matrice). Interfaccia: editor visuale della griglia (clic sulla cella → valore, colore, classe, azione), descrizioni per categoria di impatto, anteprima. Libreria di matrici aziendali; una matrice è **bloccata** una volta usata in uno studio rilasciato (si crea una nuova versione).

---

<a id="m9"></a>
## M9 — LOPA e SIL

Vedi [02-metodologie.md §7](02-metodologie.md#lopa). Librerie dedicate: **eventi iniziatori** con frequenza tipica e **IPL** con PFD tipica e criteri. Grafico a catena per scenario; riepilogo SIF/SIL; export SRS preliminare.

---

<a id="m10"></a>
## M10 — Librerie e knowledge base

**Tipi di libreria:** guideword, parametri, deviazioni standard per tipo di nodo (linea, serbatoio, pompa, scambiatore, reattore, colonna, compressore, forno), cause tipiche, conseguenze tipiche, salvaguardie, eventi iniziatori LOPA, IPL, voci di checklist, domande What-If, modi di guasto FMEA, frasi standard per raccomandazioni.

**Funzioni**
- Librerie a livello **sistema** (fornite con il programma), **organizzazione**, **studio**.
- **Promozione**: da uno studio, selezionare righe e "aggiungi alla libreria aziendale" (con approvazione dell'amministratore) → costruzione della knowledge base aziendale.
- Ricerca, tag, categorie, multilingua (stessa voce in più lingue).
- Import/export librerie in CSV/Excel/JSON.
- Pacchetto incluso di serie: obiettivo **≥ 2.500 voci di checklist** e ≥ 500 cause/salvaguardie, scritte dal progetto o da fonti di pubblico dominio, con fonte citata per ciascuna.

---

<a id="m11"></a>
## M11 — Recommendations Manager (action tracking)

**Raccomandazione:** ID (es. `HZ-2026-014-R12`), testo, motivazione, righe/scenari collegati (anche più di uno), priorità (derivata dal rischio o manuale), **responsabile**, reparto, **scadenza**, costo stimato, categoria (progettazione, procedura, formazione, manutenzione), stato.

**Workflow configurabile**
```
Proposta → Accettata ─→ In corso → Completata → Verificata → Chiusa
       └→ Rifiutata (motivazione obbligatoria, approvazione PSM)
       └→ Accettata con modifica (testo alternativo)
```
- Notifiche e-mail: assegnazione, scadenza imminente, scaduta, richiesta di verifica.
- **Evidenze di chiusura**: allegati, commenti, firma di chi verifica.
- Proroghe con motivazione e approvazione; cronologia completa.
- Dashboard: aperte/scadute per impianto, responsabile, priorità; aging; trend mensile.
- Portale "Le mie azioni" per i responsabili, senza dover aprire lo studio.
- Le raccomandazioni restano attive anche dopo la release dello studio (vivono fuori dalla release).

**Accettazione:** un responsabile può chiudere un'azione con evidenza da browser mobile in < 1 minuto.

---

<a id="m12"></a>
## M12 — Report ed export

**Report predefiniti**
1. Report completo dello studio (copertina, sommario, dati studio, team, presenze, nodi con disegni evidenziati, worksheet, LOPA, raccomandazioni, appendici).
2. Worksheet per nodo (formato tabellare classico).
3. Registro raccomandazioni (con stato attuale).
4. Riepilogo rischio: heat map iniziale/residua, top-N scenari.
5. Riepilogo LOPA e SIF/SIL.
6. Registro presenze.
7. Report "differenze" fra due release.
8. Report di portafoglio (più studi): rischio per impianto, azioni scadute.

**Funzioni:** filtri (per nodo, rischio, stato, responsabile), scelta delle colonne, raggruppamenti, intestazioni/loghi aziendali, **template di report personalizzabili** (DOCX con segnaposto, oppure HTML/Handlebars). Export **DOCX, XLSX, PDF, HTML, CSV, JSON**.

**Accettazione:** report completo di uno studio da 50 nodi in DOCX in < 30 s; l'Excel esportato è reimportabile senza perdite (round-trip).

---

<a id="m13"></a>
## M13 — Template designer

Editor amministrativo per creare/modificare metodologie senza programmare:
- **Gerarchia**: livelli, keyword, cardinalità (1-N), livelli opzionali.
- **Fogli**: quali livelli mostrare, ordine colonne, larghezze, fusioni, viste.
- **Colonne**: tipo (testo, rich text, numero, data, lista singola/multipla, utente, link, calcolato, matrice, allegato), validazioni, default, AutoType on/off, sorgente libreria.
- **Liste di valori** e **matrici** (rischio, dipendenze — *Dependency Matrix*: matrici N×M fra due liste, es. cause × salvaguardie).
- **Regole di mirroring** tra fogli/template (es. HAZOP→LOPA).
- **Form** (dati studio, raccomandazione) con campi personalizzati.
- Versionamento dei template; uno studio resta legato alla versione con cui è nato, con migrazione guidata.
- Import/export template come JSON.

---

<a id="m14"></a>
## M14 — Release management e change tracking

- **Audit trail** a livello di campo: valore precedente, nuovo, utente, timestamp, sessione. Consultabile per riga ("storia di questa cella").
- **Release**: snapshot immutabile dello studio con numero di revisione, motivo, approvatori e firme elettroniche; hash di integrità.
- **Confronto** tra due release o tra release e bozza corrente: righe aggiunte/rimosse/modificate, evidenziate.
- Lock dello studio rilasciato; nuove modifiche solo su una nuova revisione.
- Conforme ai principi di 21 CFR Part 11 (firme elettroniche, audit trail) — utile in ambito farmaceutico.

---

<a id="m15"></a>
## M15 — Sicurezza e amministrazione

- Autenticazione: locale (password + **TOTP 2FA**), **LDAP/Active Directory**, **OIDC/SAML** (Entra ID, Okta, Keycloak), Windows Integrated Auth per installazioni on-premise.
- **Ruoli** (RBAC) globali e per studio: Amministratore, PSM Manager, Facilitatore, Scriba, Membro (lettura+commento), Responsabile azione, Auditor (sola lettura).
- Permessi per sito/impianto/studio; condivisione temporanea con esterni.
- Gestione utenti, gruppi (sincronizzati da LDAP), policy password, sessioni attive.
- Configurazioni: matrici, template, librerie, SMTP, branding report, lingue abilitate, retention.
- Log di sicurezza (accessi, export, cambi permessi).

---

<a id="m16"></a>
## M16 — Internazionalizzazione

- UI tradotta (file di traduzione ICU): partenza **italiano e inglese**, poi DE, FR, ES, PT, JA, ZH, KO.
- Contenuti degli studi in qualunque lingua Unicode; supporto **right-to-left** (arabo, ebraico) nelle celle e nei report.
- Librerie con traduzioni per voce; report generabili in lingua diversa dall'interfaccia per le etichette fisse.
- Formati locali di data/numero (notazione 1E-2 sempre accettata per frequenze e PFD).

---

<a id="m18"></a>
## M18 — Import, interoperabilità e API

- **Import da Excel**: wizard di mappatura colonne → livelli della gerarchia (per migrare studi esistenti fatti in Excel o esportati da altri tool).
- **API REST** documentata (OpenAPI) per studi, righe, raccomandazioni, librerie: integrazione con CMMS (SAP PM, Maximo) per trasformare raccomandazioni in ordini di lavoro, e con sistemi MOC.
- Webhook su eventi (raccomandazione creata/scaduta/chiusa, studio rilasciato).
- Formato aperto `.phaf` (JSON zippato + allegati) documentato pubblicamente.
