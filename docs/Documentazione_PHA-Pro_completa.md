**PHA-Pro**

Documentazione tecnica e funzionale completa

Componenti dell’interfaccia, moduli, configurazione, flussi operativi, analisi del rischio, reporting e gestione delle revisioni

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>STATO DELLE FONTI</strong></p>
<p>Il report Deep Research originario identifica il prodotto come PHA-Pro. Le schermate e la documentazione pubblica confermano che le funzioni descritte appartengono alla famiglia PHA-Pro, ma il video YouTube indicato non è stato acquisito in modo leggibile in questa sessione. Di conseguenza, non viene dichiarato che le schermate esterne siano frame del video. Le differenze tra versioni sono segnalate.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

**Fonte video indicata dall’utente:** [<u>YouTube - jfCmCVNGgaU, dal minuto 01:21</u>](https://www.youtube.com/watch?v=jfCmCVNGgaU&t=81s)

Versione del documento: 1.0 \| Data: 10 novembre 2026

# Indice

> 1\. Scopo, perimetro e metodo di lettura
>
> 2\. Panoramica del software e versioni
>
> 3\. Struttura generale dell’interfaccia
>
> 4\. Amministrazione dello studio (Administration)
>
> 5\. Nodi e deviazioni
>
> 6\. Develop HAZOP Worksheet: il nucleo dell’analisi
>
> 7\. Manage Recommendations
>
> 8\. Librerie, AutoType e riuso della conoscenza
>
> 9\. Risk Systems, matrici e Heat Map
>
> 10\. Linked Diagram e collegamento ai worksheet
>
> 11\. Metodologie e template supportati
>
> 12\. Reports, stampa ed esportazione
>
> 13\. Analyze e Data Check
>
> 14\. Settings e personalizzazione
>
> 15\. Release Management, revalidation e protezione
>
> 16\. Note, allegati, marker e statistiche di cella
>
> 17\. Modello concettuale dei dati e relazioni tra moduli
>
> 18\. Guida operativa: workflow HAZOP completo
>
> 19\. Ruoli, permessi, integrazioni e limiti
>
> 20\. Troubleshooting e controlli frequenti
>
> 21\. FAQ
>
> 22\. Glossario
>
> 23\. Galleria di schermate UI e provenienza
>
> 24\. Fonti e riferimenti

Le schermate consultabili sono raccolte nella sezione 23; le fonti complete sono nella sezione 24.

# 1. Scopo, perimetro e metodo di lettura

Questo documento consolida il sommario esecutivo prodotto dalla sessione Deep Research e lo amplia con contenuti ricavati da fonti pubbliche sul software PHA-Pro. È pensato come riferimento per onboarding, formazione utente e consultazione funzionale. La struttura segue il flusso tipico di uno studio PHA/HAZOP, dalla creazione del progetto fino alla gestione delle raccomandazioni e alla pubblicazione del report.

Il report originario è stato integrato e corretto dove riportava elementi con formulazione ipotetica o non dimostrata. In particolare, nomi di estensioni file, scorciatoie, ruoli autorizzativi e alcuni comandi possono dipendere dalla release, dalla configurazione aziendale o dal template installato e non vanno considerati universali.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>AVVERTENZA SUL VIDEO</strong></p>
<p>Il collegamento YouTube è riportato integralmente nella copertina e nella bibliografia. Il recupero automatico di pagina, metadati e trascrizione non è riuscito; non è quindi possibile attribuire timestamp specifici alle funzioni qui descritte. Per lo stesso motivo, gli screenshot inseriti in appendice sono riferimenti a schermate pubblicate da fonti esterne, non immagini estratte dal video.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 1.1 Convenzioni di attendibilità

| **Etichetta**                    | **Significato**                                                                             | **Come usarla**                                                                              |
|----------------------------------|---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| Confermato dal produttore        | Funzione descritta nella pagina o nella brochure ufficiale Sphera.                          | È il livello di evidenza più alto per le funzionalità generali attuali.                      |
| Documentato in guida/manuale     | Funzione descritta in manuali PHA-Pro 8.x o in esercizi formativi reperibili pubblicamente. | Può riferirsi a una versione legacy; verificare i nomi esatti nell’installazione in uso.     |
| Osservato in screenshot pubblico | Componente visibile in un’immagine o in un report di progetto pubblicato.                   | Conferma l’esistenza visiva del componente nella versione ritratta, non in tutte le release. |
| Dedotto / da verificare          | Dettaglio plausibile ma non completamente specificato dalla fonte.                          | Non utilizzare come requisito certo senza verifica sul software installato.                  |

# 2. Panoramica del software

PHA-Pro è un applicativo di Process Hazard Analysis (PHA) e HAZOP destinato alla strutturazione degli studi di rischio di processo. La pagina ufficiale Sphera lo presenta come soluzione per identificare, valutare e controllare i rischi connessi ai processi industriali, attraverso template preformattati, librerie, collegamento dinamico tra diagrammi e worksheet, gestione delle raccomandazioni e reportistica. \[S2\]\[S3\]

La brochure ufficiale elenca template pronti per HAZOP, What-If, LOPA, determinazione SIL tramite Risk Graph e Safety Layer Matrix; cita inoltre HAZID, CHAZOP, HACCP, Dust Hazards Analysis, Security Assessments e SIMOPS tra i metodi supportati o disponibili. La disponibilità concreta può variare in base a licenza, template e pacchetto acquistato. \[S3\]

| **Area**              | **Valore funzionale**                                                         | **Output tipico**                                            |
|-----------------------|-------------------------------------------------------------------------------|--------------------------------------------------------------|
| Standardizzazione     | Modelli di studio, categorie, codici, gerarchie e librerie riutilizzabili.    | Studi coerenti tra stabilimenti e team.                      |
| Analisi tecnica       | Tracciamento di nodi, deviazioni, cause, conseguenze, salvaguardie e ranking. | Worksheet HAZOP / PHA completo.                              |
| Riduzione del rischio | Collegamento tra scenari, salvaguardie e raccomandazioni.                     | Azioni assegnabili e verificabili.                           |
| Conoscenza aziendale  | Riutilizzo di studi precedenti, knowledge library e AutoType.                 | Riduzione del reinserimento e conservazione dell’esperienza. |
| Controllo documentale | Release Management, change log, revision chain e protezione.                  | Documento approvato con tracciabilità delle modifiche.       |
| Reporting e analisi   | Esportazione report e analisi statistiche/visuali.                            | Report per workshop, revisione e management.                 |

## 2.1 Versioni: desktop legacy e offerta attuale

Le schermate reperibili mostrano più generazioni dell’interfaccia: PHA-Pro 7, PHA-Pro 8.1 e PHA-Pro 8/8.3.4. La guida utente 8.3.4 consultabile pubblicamente è datata 2 aprile 2013; una schermata pubblicata da un utente mostra PHA-Pro 8.1.0.0 con data agosto 2021. La pagina Sphera corrente descrive il prodotto senza rendere pubblica, in quella pagina, una corrispondenza completa tra ogni voce della UI legacy e la release corrente. \[S2\]\[S4\]\[S5\]\[S7\]

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>IMPORTANTE PER LA FORMAZIONE</strong></p>
<p>La documentazione dettagliata dei menu e delle schede qui sotto riguarda prevalentemente la linea desktop PHA-Pro 8.x, sulla base dei manuali pubblici disponibili. Non assumere che la UI coincida con quella di una soluzione cloud o di una release successiva senza un confronto visivo.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# 3. Struttura generale dell’interfaccia

La UI desktop documentata è organizzata intorno a una finestra principale con barra dei menu, toolbar, pannello Workspace e fogli di lavoro a schede. In un esempio di progetto reale pubblicato nel 2014 sono visibili, in alto, le schede Administration, List “Nodes”, List “Deviations”, Develop HAZOP Worksheet, Manage Recommendations, Reports, Stature, Analyze, Settings e Data Check. Il pannello Workspace a sinistra contiene Open Documents e Active Libraries. \[S8\]

## 3.1 Barra dei menu e toolbar

La barra dei menu raccoglie comandi globali per creare/aprire/salvare studi, stampare o esportare, gestire revisioni, modificare impostazioni e aprire strumenti. La toolbar offre comandi contestuali e scorciatoie grafiche. La guida utente 8.3.4 documenta l’avvio di un nuovo file tramite File \> New e l’apertura del New File Wizard; la documentazione legacy cita inoltre il comando View \> Workspace e la scorciatoia Alt+0 per mostrare/nascondere il pannello. \[S4\]

- File: creazione, apertura, chiusura, salvataggio, gestione versioni, stampa ed esportazione. I comandi esatti dipendono dalla versione.

- Edit / Modifica: operazioni di modifica e copia/incolla; nelle schede si possono anche copiare celle o righe.

- View / Visualizza: visualizzazione di Workspace, toolbar e viste disponibili.

- Insert / Inserisci: inserimento di elementi o schede, secondo il contesto della release.

- Tools / Strumenti: opzioni, protezione e funzioni di configurazione.

Non è stato possibile confermare un elenco universale completo dei menu e delle scorciatoie: l’elenco sopra è descrittivo e non va trattato come inventario esaustivo.

## 3.2 Workspace

Workspace è il pannello di navigazione ad albero. La documentazione e gli screenshot mostrano due raggruppamenti fondamentali: Open Documents, che elenca gli studi aperti, e Active Libraries, che elenca le librerie caricate e attivabili. In un progetto di esempio sono presenti librerie HAZOP, LOPA, HACCP, PHA, What-If, Knowledge Base, MOC, Process Safety Information e altre raccolte tematiche. \[S8\]

| **Nodo Workspace**        | **Scopo**                                       | **Operazioni tipiche**                                                                        |
|---------------------------|-------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Open Documents            | Raccoglie i file di studio attualmente aperti.  | Selezionare uno studio; espandere i suoi fogli; passare rapidamente tra documenti.            |
| Active Libraries          | Elenca librerie e raccolte di contenuti attive. | Attivare/disattivare librerie disponibili; riutilizzare elementi o suggerimenti nelle schede. |
| Foglio / scheda di studio | Rappresenta una sezione del documento aperto.   | Aprire la vista, modificarne i dati, accedere alle proprietà o al menu contestuale.           |

L’interazione puntuale (doppio clic, menu contestuale, ridimensionamento del pannello) è coerente con il paradigma ad albero desktop. La visibilità del Workspace è documentata come commutabile; non tutte le voci di menu contestuali sono state verificate in ogni versione. \[S4\]

## 3.3 Schede principali osservate

| **Scheda / area**       | **Funzione prevalente**                                                            | **Evidenza**                                                                                           |
|-------------------------|------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Administration          | Metadati del progetto, facility, team, sessioni, disegni e informazioni di studio. | Screenshot PHA-Pro 8 in un report HAZOP/HAZID 2014. \[S8\]                                             |
| List “Nodes”            | Elenco strutturato dei nodi di processo.                                           | Esercizi PHA-Pro 8. \[S5\]                                                                             |
| List “Deviations”       | Elenco delle deviazioni applicabili ai nodi.                                       | Esercizi PHA-Pro 8. \[S5\]                                                                             |
| Develop HAZOP Worksheet | Foglio centrale con cause, conseguenze, ranking, salvaguardie e raccomandazioni.   | Screenshot pubblici PHA-Pro. \[S6\]\[S7\]                                                              |
| Manage Recommendations  | Registro centralizzato delle raccomandazioni.                                      | Brochure Sphera ed esercizi. \[S3\]\[S5\]                                                              |
| Reports                 | Stampa, esportazione e raccolte di report.                                         | Guida ed esercizi. \[S4\]\[S5\]                                                                        |
| Analyze                 | Analisi statistica e grafica dei dati dello studio.                                | Esercizi PHA-Pro 8. \[S5\]                                                                             |
| Settings                | Configurazione di struttura dati, template, codici, categorie e matrici.           | Guida ed esercizi. \[S4\]\[S5\]                                                                        |
| Data Check              | Verifiche di completezza e regole sui dati dello studio.                           | Esercizi PHA-Pro 8. \[S5\]                                                                             |
| Stature                 | Voce presente in una schermata di PHA-Pro 8.                                       | Funzione precisa non verificata dalle fonti consultate; da non confondere con una funzione confermata. |

# 4. Amministrazione dello studio (Administration)

Administration raccoglie le informazioni di contesto necessarie a identificare e governare uno studio. Uno screenshot di un report industriale mostra un pannello General con campi Facility Information: Company, Business Unit, Facility, Project ID e Project Name, oltre a Study Duration con Start Date ed End Date. La stessa schermata contiene la navigazione Workspace e le schede di lavoro. \[S8\]

## 4.1 Dati identificativi

| **Campo osservato**   | **Descrizione**                                         | **Esempio documentato**                                      |
|-----------------------|---------------------------------------------------------|--------------------------------------------------------------|
| Company               | Organizzazione proprietaria o committente dello studio. | Indian Oil Corporation Limited. \[S8\]                       |
| Business Unit         | Unità organizzativa o area aziendale.                   | Pattikalan. \[S8\]                                           |
| Facility              | Impianto o sito oggetto dell’analisi.                   | Indane LPG Bottling Plant. \[S8\]                            |
| Project ID            | Identificativo univoco del progetto.                    | J0519. \[S8\]                                                |
| Project Name          | Titolo esteso dello studio.                             | HAZOP/HAZID, QRA and ERDMP for Indane Bottling Plant. \[S8\] |
| Start Date / End Date | Periodo di esecuzione o durata prevista dello studio.   | 23-04-2014 / 23-04-2014. \[S8\]                              |

Ulteriori fogli amministrativi possono contenere metodologia, descrizione di processo, partecipanti, sessioni, disegni e cronologia di revalidazione. La presenza e il nome dei fogli variano in base al template e alla personalizzazione dello studio. Gli End-User Exercises mostrano un wizard che chiede company, business unit, facility, Project ID, Project Name, membri del team e dati relativi a sessioni e drawings. \[S5\]

## 4.2 Team, partecipanti e sessioni

La composizione del team di studio serve a documentare chi ha partecipato all’analisi, con eventuali informazioni di contatto e appartenenza organizzativa. Gli esercizi formativi mostrano colonne di contatto (ad esempio email e dipartimento) e la possibilità di allegare documenti ai record dei partecipanti. Le sessioni permettono di registrare gli incontri di analisi. \[S5\]

- Inserire i membri del team e i relativi dati anagrafici/organizzativi richiesti dal template.

- Registrare le sessioni e le informazioni richieste dal flusso aziendale.

- Mantenere la corrispondenza fra partecipanti, presenze e report di studio.

Non sono disponibili evidenze sufficienti per descrivere una matrice universale di ruoli applicativi o permessi per singolo utente: il fatto che il programma sia desktop e single-user in alcune distribuzioni non implica che ogni implementazione aziendale abbia lo stesso modello di controllo.

# 5. Nodi e deviazioni

## 5.1 List “Nodes”

La scheda Nodes definisce la scomposizione dell’impianto in porzioni analizzabili, chiamate nodi. Ogni nodo deve avere un’identità stabile e una descrizione che ne chiarisca confini, funzione e intento di progetto. Gli esercizi PHA-Pro 8 mostrano inserimento di nuovi nodi, compilazione del campo Type (es. Heat Exchanger) e riuso di nodi da studi preesistenti. \[S5\]

| **Elemento**                  | **Scopo**                                                                        | **Buona pratica**                                                |
|-------------------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------|
| Node ID / identificativo      | Riconoscere univocamente il nodo.                                                | Usare una convenzione coerente con P&ID e documenti di impianto. |
| Nome del nodo                 | Descrivere in modo breve la porzione di processo.                                | Evitare nomi ambigui o duplicati.                                |
| Descrizione / design intent   | Chiarire funzione, confini e condizioni operative.                               | Indicare apparecchiature e linee comprese nel nodo.              |
| Type / tipologia              | Classificare l’elemento (es. line, vessel, exchanger), se previsto dal template. | Usare le categorie della libreria aziendale.                     |
| Disegni e documenti collegati | Collegare il nodo ai riferimenti tecnici.                                        | Verificare revisioni e validità dei P&ID allegati.               |

Operativamente: creare o importare i nodi; verificare che coprano tutto il perimetro di studio; controllare numerazione e documenti di riferimento; poi associare le deviazioni. I nomi precisi delle colonne non sono universali e sono personalizzabili.

## 5.2 List “Deviations”

La scheda Deviations elenca le deviazioni da considerare per i nodi. La logica HAZOP parte dall’intento di progetto e applica parole guida (guidewords) a parametri di processo, come portata, pressione, temperatura, livello, composizione o direzione del flusso. Gli esercizi mostrano ad esempio deviazioni “High Pressure”, “Low or No Flow” e la possibilità di aggiungere o eliminare righe/celle. \[S5\]

| **Esempio di parametro** | **Esempio di deviazione**          | **Domanda analitica**                                                       |
|--------------------------|------------------------------------|-----------------------------------------------------------------------------|
| Portata                  | No Flow / Low Flow / More Flow     | Che cosa accade se il flusso è assente, insufficiente o eccessivo?          |
| Pressione                | High Pressure / Low Pressure       | Quali cause possono generare pressione fuori campo?                         |
| Temperatura              | High Temperature / Low Temperature | Quali conseguenze derivano da condizioni termiche anomale?                  |
| Livello                  | High Level / Low Level / No Level  | L’apparecchiatura può traboccare, svuotarsi o perdere controllo?            |
| Composizione             | Other Than / Contamination         | Un componente indesiderato o una concentrazione anomala può creare rischio? |

Il software consente di riutilizzare liste e contenuti da libreria, ma la selezione delle deviazioni pertinenti resta una decisione tecnica del team. L’applicazione automatica di tutte le guidewords senza giudizio può generare righe non significative.

# 6. Develop HAZOP Worksheet: il nucleo dell’analisi

Il foglio HAZOP raccoglie per ogni scenario il collegamento fra nodo, deviazione, causa, conseguenza, salvaguardia, ranking e azione proposta. Le schermate pubbliche mostrano una griglia ampia e tabellare, con colonne per Causes, Consequences, consequence category, valutazione prima della riduzione del rischio, Safeguards, Recommendations, Responsibility e valutazione dopo la riduzione. \[S6\]\[S7\]\[S9\]

| **Campo / colonna**   | **Significato**                                        | **Indicazioni operative**                                                                 |
|-----------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------|
| Node                  | Nodo cui appartiene lo scenario.                       | Controllare che il riferimento sia coerente con Nodes.                                    |
| Deviation             | Scostamento dall’intento di progetto.                  | Usare un termine chiaro e coerente con la libreria.                                       |
| Cause(s)              | Evento o guasto che genera la deviazione.              | Descrivere cause specifiche, non formule generiche.                                       |
| Consequence(s)        | Esito potenziale della deviazione.                     | Separare effetti su persone, ambiente, asset e produzione quando il template lo richiede. |
| Consequence Category  | Categoria della conseguenza.                           | Usare codici aziendali; gli esercizi mostrano categorie ES, PS, EI, CL, PL.               |
| Severity (S)          | Gravità della conseguenza.                             | Applicare definizioni e scala aziendale.                                                  |
| Likelihood (L)        | Probabilità/frequenza dello scenario.                  | Usare la base dati e i criteri definiti nella matrice di rischio.                         |
| Risk Ranking / RR     | Classe risultante dalla matrice o regola di calcolo.   | Verificare la regola configurata: non assumere sempre S×L.                                |
| Safeguards            | Misure preventive o mitigative già esistenti.          | Descrivere barriera, funzione, indipendenza e riferimento tecnico.                        |
| HAZOP Recommendations | Azioni nuove o aggiuntive proposte dal team.           | Formulare un’azione verificabile con output atteso.                                       |
| Responsibility        | Responsabile dell’azione.                              | Assegnare ruolo o persona secondo processo aziendale.                                     |
| After Risk Reduction  | Ranking dopo le salvaguardie / interventi considerati. | Non ridurre il ranking senza motivare le barriere e la loro efficacia.                    |
| Remark / Comment      | Note, assunzioni o chiarimenti.                        | Usare per precisare ambito, ipotesi e motivazioni.                                        |

## 6.1 Valutazione del rischio inerente e residuo

Molti template distinguono il rischio prima e dopo l’applicazione/valutazione delle salvaguardie. Nei fogli pubblici si vedono intestazioni simili a Before Risk Reduction e After Risk Reduction, ciascuna con Severity, Likelihood e Risk Ranking. La scala, la logica cromatica e la regola di calcolo vanno configurate nel Risk System aziendale: non esiste una singola matrice valida per tutti i progetti. \[S5\]\[S9\]

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>CONTROLLO TECNICO</strong></p>
<p>Il risk ranking non deve essere ridotto automaticamente solo perché è stata inserita una salvaguardia nel campo testo. Il team deve verificare che la misura esista, sia applicabile allo scenario, sia mantenuta e abbia un’efficacia credibile. La matrice e i criteri sono parte della metodologia aziendale, non una proprietà universale del software.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 6.2 Modifica e formattazione del worksheet

Gli esercizi PHA-Pro 8 documentano un’ampia flessibilità di presentazione: rinominare intestazioni, mostrare/nascondere colonne, spostarle con drag-and-drop, modificare formato di colonna e intestazione, applicare formattazioni multiple e inserire nuove schede. Possono essere configurati anche breakdown e filtri di visualizzazione/stampa. \[S5\]

- Per cambiare il nome di una colonna: menu contestuale sull’intestazione e scelta del nome alternativo (la voce esatta dipende dalla release).

- Per aggiungere una colonna: proprietà della scheda/Sheet Properties e selezione dei campi disponibili, se previsti dal modello.

- Per nascondere o mostrare colonne: comando contestuale sulle intestazioni.

- Per modificare il layout: trascinare le colonne e usare i controlli di formato del foglio.

- Per filtrare: impostare i filtri in modo che si applichino sia alla vista a schermo sia al report esportato, quando richiesto.

# 7. Manage Recommendations

Recommendations Manager raccoglie le raccomandazioni generate dai fogli di analisi in un elenco centralizzato. Sphera la indica come funzione di gestione completa delle raccomandazioni; gli esercizi PHA-Pro 8 mostrano la scheda Manage Recommendations e la possibilità di aggiungere colonne, ad esempio ranking massimo o categorie, e di organizzare i campi nella vista. \[S3\]\[S5\]

| **Dato tipico**        | **Descrizione**                                                       | **Uso gestionale**                                   |
|------------------------|-----------------------------------------------------------------------|------------------------------------------------------|
| Recommendation ID      | Identificativo dell’azione.                                           | Tracciabilità e collegamento al worksheet.           |
| Descrizione            | Azione richiesta.                                                     | Deve essere specifica, misurabile e assegnabile.     |
| Priority               | Priorità definita dal metodo aziendale.                               | Ordina gli interventi in base al livello di urgenza. |
| Category               | Famiglia dell’azione (es. engineering, operations, maintenance, I&C). | Analisi per disciplina e assegnazione.               |
| Responsibility / Owner | Funzione o persona responsabile.                                      | Gestione e follow-up.                                |
| Status                 | Stato dell’azione, se previsto dalla configurazione.                  | Monitoraggio avanzamento e chiusura.                 |
| Due date / target date | Scadenza o data prevista.                                             | Controllo ritardi e pianificazione.                  |
| Comments / evidence    | Note, evidenze o riferimenti di chiusura.                             | Documentare completamento e verifica.                |

La relazione funzionale è bidirezionale a livello di studio: l’azione nasce tipicamente nel worksheet a fronte di uno scenario; l’elenco master consente la gestione aggregata, evitando di dover ricercare ogni raccomandazione foglio per foglio. I dettagli di workflow e i campi effettivi devono essere verificati sul template installato.

## 7.1 Processo consigliato

> **1.** Inserire la raccomandazione nello scenario che la motiva.
>
> **2.** Verificare che il testo descriva un deliverable e un criterio di completamento.
>
> **3.** Assegnare owner e priorità in base alle regole del sito.
>
> **4.** Definire data obiettivo e categoria, se previste.
>
> **5.** Aggiornare lo stato durante il follow-up.
>
> **6.** Registrare l’evidenza di chiusura e verificare che il rischio sia stato rivalutato quando necessario.

# 8. Librerie, AutoType e riuso della conoscenza

Le knowledge libraries sono raccolte riutilizzabili di dati, check-list, guidewords, misure, categorie e contenuti tecnici. La pagina Sphera descrive le librerie come supporto per accelerare le valutazioni e preservare conoscenza ingegneristica; una schermata di progetto reale elenca librerie HAZOP, LOPA, HACCP, JSA, PHA, MOC, process safety information, RMP, revalidation e standards/protocol. \[S2\]\[S3\]\[S8\]

AutoType permette di riutilizzare valori e descrizioni predefinite durante la compilazione dei campi, riducendo la variabilità lessicale e il tempo di inserimento. Sphera cita AutoType e Copy tra le funzionalità potenziate; esercizi formativi mostrano il comando Copy From per selezionare elementi da un elenco e riutilizzarli. \[S3\]\[S5\]

| **Componente**     | **Funzione**                                             | **Beneficio / cautela**                                                      |
|--------------------|----------------------------------------------------------|------------------------------------------------------------------------------|
| Librerie standard  | Contenuti precompilati per metodi e discipline.          | Velocizzano l’avvio; devono essere selezionate in base allo studio.          |
| Librerie aziendali | Contenuti validati dall’organizzazione.                  | Uniformano il modo di documentare gli studi.                                 |
| AutoType           | Suggerisce o inserisce valori standardizzati nei campi.  | Riduce refusi; verificare che il suggerimento sia applicabile al contesto.   |
| Copy / Copy From   | Riutilizza record o righe da altri studi o librerie.     | Può conservare informazioni collegate; controllare riferimenti e pertinenza. |
| Active Libraries   | Indica quali librerie sono attive nel contesto del file. | La selezione influisce sulle opzioni disponibili all’utente.                 |

# 9. Risk Systems, matrici e Heat Map

Risk Systems governa scale, codici, descrizioni e matrici utilizzate per attribuire i ranking. Gli esercizi PHA-Pro 8 mostrano la creazione di una 2D Risk Matrix, la definizione dei valori per Severity, Likelihood e Risk Ranking, la modifica degli assi e dei colori e il collegamento della matrice a una voce della gerarchia (ad esempio Consequences). \[S5\]

La matrice di rischio classifica gli scenari incrociando severità e probabilità/frequenza. Le schermate ufficiali Sphera più recenti mostrano anche una Hybrid HAZOP Heat Map con livelli multipli e indicatori aggregati di studio, mentre altre schermate legacy mostrano matrici 2D colorate. \[S3\]\[S10\]

| **Elemento di configurazione** | **Descrizione**                                                       |
|--------------------------------|-----------------------------------------------------------------------|
| Severity                       | Scala di gravità e relative definizioni.                              |
| Likelihood                     | Scala di probabilità o frequenza e relative soglie.                   |
| Risk Ranking                   | Codici e descrizioni del risultato di rischio.                        |
| Matrix cells                   | Associazione tra combinazioni di Severity/Likelihood e ranking.       |
| Colors                         | Codifica visiva per classi di rischio.                                |
| Usage / Linked Item            | Associazione della matrice al campo o elemento a cui deve applicarsi. |
| Axis order / side              | Orientamento e ordine degli assi, secondo il modello configurato.     |

I criteri di esempio presenti negli esercizi (ad esempio categorie A/C/N/U o scale numeriche) sono dimostrativi e non devono essere copiati senza l’approvazione del responsabile HSE/process safety. \[S5\]

# 10. Linked Diagram e collegamento ai worksheet

PHA-Pro dichiara il collegamento dinamico tra diagrammi e worksheet. Gli esercizi descrivono la creazione di una nuova scheda Linked Diagram, la scelta dei tipi di elementi da rappresentare, il trascinamento dei nodi nell’area di disegno e il collegamento di elementi di dettaglio. Forme, frecce, colore, testo e proprietà grafiche possono essere modificati; gli elementi restano associati ai nodi del foglio Nodes. \[S3\]\[S5\]

> **1.** Aprire l’area Administration e inserire una nuova scheda di tipo Linked Diagram (il nome del comando può variare).
>
> **2.** Assegnare un nome alla scheda e scegliere gli elementi dello studio da esporre, ad esempio Nodes e Types.
>
> **3.** Trascinare i nodi dal pannello Study Items all’area grafica.
>
> **4.** Aggiungere forme e frecce per rappresentare apparecchiature e connessioni.
>
> **5.** Aggiornare formato e testo delle forme, mantenendo i riferimenti corretti.
>
> **6.** Verificare che la selezione del diagramma e la scheda Nodes riflettano la stessa struttura.

Il Linked Diagram non sostituisce P&ID o disegni ingegneristici controllati: è una rappresentazione collegata dello studio e deve rinviare ai documenti sorgente ufficiali per i dettagli di progettazione.

# 11. Metodologie e template supportati

| **Metodo / template**                                       | **Finalità sintetica**                                                                                            | **Nota**                                                                   |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| HAZOP                                                       | Esaminare deviazioni dall’intento di progetto tramite guidewords, individuando cause, conseguenze e salvaguardie. | Il worksheet HAZOP è il flusso più documentato nelle schermate consultate. |
| What-If / Checklist                                         | Esplorare scenari con domande strutturate e checklist.                                                            | Disponibilità citata da Sphera e dai partner.                              |
| PHA / PrHA                                                  | Valutazione preliminare o strutturata dei pericoli di processo.                                                   | Il contenuto del template determina il dettaglio.                          |
| LOPA                                                        | Valutare gli strati indipendenti di protezione e la riduzione del rischio.                                        | Sphera indica template collegabili a HAZOP.                                |
| SIL Determination                                           | Supportare la determinazione del livello SIL mediante Risk Graph o Safety Layer Matrix.                           | Confermato dalla brochure 2025.                                            |
| HAZID / CHAZOP / HACCP / DHA / SIMOPS / Security Assessment | Metodi specialistici di identificazione e valutazione dei rischi.                                                 | Elencati nella brochure; verifica dei moduli/licenze necessari.            |

# 12. Reports, stampa ed esportazione

La reportistica consente di pubblicare singole schede, worksheet o raccolte composte. La brochure ufficiale indica esportazione in HTML, Word e Excel. Gli esercizi PHA-Pro 8 descrivono anche XML, la scelta di output di stampa, intestazioni/piè di pagina, anteprima e report collection. La specifica disponibilità di PDF, XML o altri formati dipende dalla versione e dal percorso di stampa/esportazione. \[S3\]\[S5\]

| **Funzione**               | **Descrizione**                                                       | **Aspetti da controllare**                                                |
|----------------------------|-----------------------------------------------------------------------|---------------------------------------------------------------------------|
| Print / Print Active Sheet | Stampa o genera output della scheda attiva o di un insieme di schede. | Selezione corretta dello studio, della scheda e delle opzioni di output.  |
| Print Preview              | Anteprima dell’output prima della pubblicazione.                      | Controllare interruzioni pagina, colonne e contenuti troncati.            |
| Output Type                | Scelta del formato o della destinazione di output.                    | Confermare i formati realmente disponibili nella release installata.      |
| Headers / Footers          | Configurazione di intestazioni e piè pagina con campi dinamici.       | Inserire titolo, azienda, data di stampa, numerazione e logo se previsto. |
| Filters                    | Applicazione di filtri alla vista e/o al report esportato.            | Controllare l’ambito del filtro per evitare omissioni involontarie.       |
| Report Collection          | Raccolta personalizzata di schede da produrre insieme.                | Definire ordine, contenuto e destinatari.                                 |
| Word / Excel / HTML        | Formati documentali e dati esportabili citati dal produttore.         | Controllare il risultato esportato prima della distribuzione.             |
| XML                        | Formato indicato negli esercizi legacy.                               | Non assumere che sia presente in tutte le versioni.                       |

# 13. Analyze e Data Check

## 13.1 Analyze

L’area Analyze fornisce una lettura aggregata dei dati di studio attraverso statistiche e grafici. Gli esercizi formativi la indicano come punto di consultazione per la ripartizione statistica e grafica delle informazioni. Gli indicatori e i grafici dipendono dal template, dalle colonne configurate e dai calcoli previsti. \[S5\]

- Analisi del numero di nodi, deviazioni, cause, scenari e raccomandazioni, quando configurate.

- Distribuzione dei ranking e delle categorie di rischio.

- Aggregazione o statistica di colonne numeriche, secondo le funzioni previste.

Non viene fornito un elenco universale di grafici o metriche: le schermate effettive vanno verificate nel sistema.

## 13.2 Data Check

Data Check permette di esaminare la completezza e la coerenza dei dati e di evidenziare celle mancanti o regole non rispettate. Gli esercizi lo descrivono come strumento per elencare celle vuote o altre regole definite. \[S5\]

- Usarlo prima di approvare o distribuire un report.

- Interpretare ogni segnalazione in base alla regola e alla criticità del campo.

- Correggere i dati oppure documentare formalmente le eccezioni ammesse.

# 14. Settings e personalizzazione

Settings consente di configurare come è costruito e presentato lo studio. Gli esercizi e la documentazione PHA-Pro descrivono un modello personalizzabile: gerarchie, sheet, grid, breakdown, risk systems, codici e categorie, data dictionary, grafici, form e formule. \[S4\]\[S5\]\[S11\]

| **Area di configurazione**  | **Cosa controlla**                                | **Esempi d’uso**                                                             |
|-----------------------------|---------------------------------------------------|------------------------------------------------------------------------------|
| Project Settings / Sheets   | Struttura e proprietà delle schede.               | Aggiungere o rimuovere schede; gestire colonne e intestazioni.               |
| Hierarchy                   | Relazioni logiche tra livelli di dati.            | Nodi \> deviazioni \> cause \> conseguenze / salvaguardie / raccomandazioni. |
| Grid / Breakdown            | Presentazione tabellare, raggruppamento e filtri. | Mostrare una vista per nodo o per deviazione.                                |
| Risk Systems                | Scale, codici, matrici e criteri.                 | Allineare la valutazione al metodo aziendale.                                |
| Codes and Categories        | Valori controllati e liste a tendina.             | Categorie di conseguenza e di raccomandazione.                               |
| Libraries / Data Dictionary | Vocabolari e oggetti riutilizzabili.              | Standardizzare valori e suggerimenti.                                        |
| Forms / Additional Sheets   | Schede informative e moduli supplementari.        | Registrare informazioni specialistiche.                                      |
| Charts / Formulas           | Analisi e calcoli configurati.                    | Visualizzazioni o statistiche personalizzate.                                |

La possibilità di personalizzazione è un punto di forza ma comporta un rischio di governance: modifiche ai template, alle scale e alle formule possono cambiare la comparabilità fra studi. È raccomandabile gestire le configurazioni come asset controllati, con approvazione, test e tracciabilità.

# 15. Release Management, revalidation e protezione

## 15.1 Release Management

La gestione delle release consente di approvare una bozza e rendere tracciabili le modifiche successive. Gli esercizi PHA-Pro 8 descrivono il comando File \> Release Management \> Approve this Draft e mostrano il passaggio di stato da Draft a una versione approvata (esempio A.0). Sono inoltre citati View Change Log e View Revision Chain. \[S5\]

| **Funzione**                   | **Scopo**                                               | **Controllo raccomandato**                                                |
|--------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------|
| Draft                          | Stato di lavoro non ancora approvato.                   | Verificare contenuti e controlli prima dell’approvazione.                 |
| Approve this Draft             | Approva la bozza e crea una release.                    | Usare un approvatore previsto dalla procedura aziendale.                  |
| Change Log                     | Elenca le modifiche registrate.                         | Rivedere autore, contenuto e momento del cambiamento.                     |
| Revision Chain                 | Mostra la catena di revisioni/versioni.                 | Verificare quale versione è vigente e quali la precedono.                 |
| Modifica su versione approvata | Può generare un avviso e una nuova traccia di modifica. | Non alterare documenti approvati senza seguire il processo MOC/revisione. |

## 15.2 Revalidation

PHA-Pro 8 include riferimenti a worksheet di Revalidation History e a marker/checkmark per indicare che una cella o un contenuto è stato riesaminato. Gli esercizi mostrano l’aggiunta di note, allegati e indicatori di revalidation tramite la toolbar. \[S5\]

La revalidazione non equivale automaticamente a una nuova valutazione tecnica completa: il significato del marker, i criteri e la responsabilità devono essere definiti dalla procedura aziendale.

## 15.3 Protection

Gli esercizi descrivono un’area Tools \> Protection con tre tipologie di funzionalità di sicurezza, senza fornire nel testo acquisito un inventario sufficientemente completo per nominare le tre modalità con certezza. Non si attribuisce quindi al software una matrice dettagliata di ruoli o permessi che non sia stata verificata. \[S5\]

# 16. Note, allegati, marker e statistiche di cella

Gli esercizi PHA-Pro 8 mostrano la possibilità di associare note a celle, allegare file tramite icona a graffetta e inserire un segno di revalidation. Viene inoltre citata la possibilità di calcolare statistiche per colonne, ad esempio valori massimi o minimi e somme, con funzioni disponibili in base al tipo di dato. \[S5\]

- Note: aggiungono contesto senza alterare il contenuto della cella principale.

- Attachments: collegano evidenze o documenti di supporto. Verificare che i file allegati siano controllati e aggiornati.

- Revalidation marker: segnala il riesame secondo una procedura configurata.

- Statistics: producono aggregazioni utili per reporting e priorità; occorre verificare la semantica del calcolo.

# 17. Modello concettuale dei dati e relazioni tra moduli

La struttura funzionale tipica dello studio può essere letta come una gerarchia. La configurazione esatta delle relazioni è personalizzabile, ma il flusso più comune è: studio e contesto amministrativo → nodi → deviazioni → cause → conseguenze → valutazione del rischio → salvaguardie → raccomandazioni → follow-up e report. Le schermate e gli esercizi documentano collegamenti tra worksheet, Nodes, matrice, library items e recommendation manager. \[S5\]\[S8\]

| **Livello**             | **Contenuto**                                                 | **Collegamenti a valle**               |
|-------------------------|---------------------------------------------------------------|----------------------------------------|
| Studio / Administration | Identità del progetto, sito, team, metodologia, documenti.    | Tutti i fogli dello studio.            |
| Node                    | Sezione di processo analizzata.                               | Deviazioni e diagrammi collegati.      |
| Deviation               | Scostamento da intento o condizione operativa.                | Cause e scenari.                       |
| Cause                   | Meccanismo che innesca la deviazione.                         | Conseguenze e salvaguardie.            |
| Consequence / Scenario  | Effetto potenziale su persone, ambiente, asset o operatività. | Categoria e matrice di rischio.        |
| Risk ranking            | Valutazione secondo criteri configurati.                      | Heat map, analisi e priorità.          |
| Safeguard               | Misura esistente di prevenzione/mitigazione.                  | Rischio dopo riduzione e verifiche.    |
| Recommendation          | Azione necessaria o migliorativa.                             | Owner, priorità, stato e follow-up.    |
| Report / Release        | Output controllato dello studio.                              | Distribuzione e revisione documentale. |

## 17.1 Architettura funzionale sintetica

| **Fase**            | **Input principale**                          | **Output / modulo**              |
|---------------------|-----------------------------------------------|----------------------------------|
| 1\. Impostazione    | Dati di impianto, metodologia, team, disegni. | Administration / New File Wizard |
| 2\. Scomposizione   | P&ID, confini e intento di progetto.          | Nodes                            |
| 3\. Identificazione | Guidewords e parametri di processo.           | Deviations                       |
| 4\. Valutazione     | Cause, conseguenze, salvaguardie e ranking.   | Develop HAZOP Worksheet          |
| 5\. Azioni          | Raccomandazioni e responsabilità.             | Manage Recommendations           |
| 6\. Verifica        | Regole di completezza e indicatori.           | Data Check / Analyze             |
| 7\. Pubblicazione   | Schede, filtri, intestazioni e formato.       | Reports / Export                 |
| 8\. Governance      | Approvazione, change log e revalidation.      | Release Management / Protection  |

# 18. Guida operativa: workflow HAZOP completo

> **1.** Preparare il perimetro: definire impianto, unità, progetto, obiettivi, standard di riferimento e disegni aggiornati.
>
> **2.** Creare il file di studio con File \> New / New File Wizard e selezionare il template HAZOP appropriato.
>
> **3.** Compilare Administration: company, business unit, facility, project ID, project name, durata, team, sessioni e documenti.
>
> **4.** Caricare o attivare le librerie pertinenti nel Workspace; verificare le librerie visibili nella sezione Active Libraries.
>
> **5.** Compilare Nodes: identificare e descrivere i nodi, con confini e riferimenti documentali.
>
> **6.** Compilare Deviations: applicare guidewords ai parametri pertinenti e selezionare le deviazioni significative.
>
> **7.** Aprire Develop HAZOP Worksheet: per ciascuna combinazione nodo/deviazione sviluppare cause, conseguenze e scenari.
>
> **8.** Valutare il rischio con la matrice configurata; registrare ranking inerente secondo i criteri aziendali.
>
> **9.** Elencare le salvaguardie esistenti e verificare la loro adeguatezza; formulare le raccomandazioni dove necessario.
>
> **10.** Assegnare responsabilità, priorità e date obiettivo nel Recommendations Manager.
>
> **11.** Usare Analyze e Data Check per esaminare distribuzioni e completezza dei dati.
>
> **12.** Generare report selezionando schede, filtri, output e intestazioni; verificare l’anteprima e il file esportato.
>
> **13.** Completare revisione tecnica, approvare la bozza con Release Management e archiviare la versione approvata.
>
> **14.** Gestire il follow-up delle raccomandazioni e la successiva revalidazione secondo la procedura del sito.

## 18.1 Esempio sintetico di scenario

| **Campo**        | **Esempio illustrativo (non è un record universale)**                                                            |
|------------------|------------------------------------------------------------------------------------------------------------------|
| Node             | Linea di alimentazione a uno stripper.                                                                           |
| Deviation        | Low / No Flow.                                                                                                   |
| Cause            | Pompa ferma; valvola di controllo bloccata; linea ostruita; valvola manuale chiusa.                              |
| Consequence      | Perdita di alimentazione all’apparecchiatura; possibile accumulo o instabilità a monte.                          |
| Safeguards       | Allarme/interblocco di livello, valvola di controllo, PSV se applicabile.                                        |
| Recommendation   | Valutare un flow switch sulla linea e un allarme high-high sul recipiente a monte, dopo verifica ingegneristica. |
| Risk             | Assegnare severity, likelihood e ranking usando la matrice del sito.                                             |
| Owner / Due date | Responsabile e data da definire in sede di workshop.                                                             |

L’esempio riprende uno scenario mostrato in una schermata pubblica di worksheet PHA-Pro; il contenuto tecnico va ricalcolato per l’impianto reale e non deve essere copiato come prescrizione progettuale. \[S6\]

# 19. Ruoli, permessi, integrazioni e limiti

## 19.1 Ruoli e permessi

Le fonti consultate non consentono di definire una matrice ruoli-permessi completa e valida per tutte le distribuzioni di PHA-Pro. Le funzioni di Release Management e Protection indicano un’attenzione al controllo documentale e all’accesso, ma i diritti concreti dipendono dalla configurazione, dalla release e dal modello di licenza. Evitare quindi di assegnare in questo documento privilegi quali “admin”, “facilitator” o “approver” come ruoli tecnici nativi se non sono stati verificati nell’installazione.

## 19.2 Integrazioni e formati

Le funzionalità pubblicizzate includono l’esportazione di report in HTML, Word ed Excel, il collegamento diagrammi-worksheet e template HAZOP/LOPA collegati. Non è stato verificato un elenco di API pubbliche, connettori ERP/CMMS o interfacce di sincronizzazione automatica per la specifica versione desktop ritratta. \[S3\]

## 19.3 Limiti di questa documentazione

- Il video YouTube non è stato acquisito: nessuno screenshot del documento è attribuito al video.

- Le schermate provengono da pagine prodotto, screenshot pubblici e report di progetto di epoche differenti.

- Il manuale 8.3.4 è una guida legacy del 2013: alcuni nomi di menu e comportamenti possono essere superati.

- I campi mostrati nei worksheet dipendono dal template e dalle personalizzazioni aziendali.

- Non sono dichiarati come confermati i dettagli non documentati su ruoli, permessi granulari, API, formati file proprietari o moduli opzionali.

# 20. Troubleshooting e controlli frequenti

| **Problema / sintomo**                              | **Possibile causa**                                                                   | **Verifica / azione consigliata**                                                      |
|-----------------------------------------------------|---------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| Libreria o suggerimento non compare                 | Libreria non attiva oppure valore non presente.                                       | Controllare Active Libraries e la libreria selezionata; verificare che il dato esista. |
| Il worksheet non mostra una colonna                 | Colonna nascosta o non prevista dal template.                                         | Aprire le proprietà della scheda e verificare la selezione delle colonne.              |
| Il risk ranking non corrisponde alle aspettative    | Matrice, assi, soglie o formula non configurati come atteso.                          | Controllare Risk Systems, matrice associata e criteri di Severity/Likelihood.          |
| Una raccomandazione non compare nel registro master | La cella non è riconosciuta come record raccomandazione o la scheda non è aggiornata. | Controllare campo e collegamento al Recommendations Manager.                           |
| Il report omette righe                              | Filtri applicati solo alla vista o all’output; colonne non incluse.                   | Controllare ambito dei filtri, selezione delle schede e anteprima.                     |
| Il report è difficile da leggere                    | Colonne troppo larghe, orientamento o intestazioni non ottimizzati.                   | Modificare layout, formattazione, pagina e intestazioni.                               |
| Modifica a documento approvato                      | Versione rilasciata e controllo modifiche attivo.                                     | Seguire Release Management e verificare Change Log / Revision Chain.                   |
| Data Check segnala celle vuote                      | Campi obbligatori o controlli configurati non soddisfatti.                            | Correggere o documentare formalmente l’eccezione.                                      |
| Diagramma e Nodes non sembrano allineati            | Collegamento incompleto o modifica non riflessa.                                      | Verificare associazioni degli elementi e nomi/ID dei nodi.                             |

# 21. FAQ

**PHA-Pro è solo un software HAZOP?**

> No. Il produttore elenca template e metodi ulteriori, tra cui What-If, LOPA, SIL Determination, HAZID, CHAZOP, HACCP, DHA e SIMOPS. La disponibilità va verificata in base al contratto e alla configurazione. \[S3\]

**Tutti i worksheet hanno le stesse colonne?**

> No. PHA-Pro è configurabile. Le colonne visibili dipendono dal metodo, dal template e dalle impostazioni del progetto. \[S5\]

**Il ranking è sempre calcolato moltiplicando severità e probabilità?**

> Non si può assumere. Le regole sono definite dalla matrice e dalla configurazione del Risk System.

**Le raccomandazioni sono gestite solo nel worksheet?**

> No. La funzione Recommendations Manager offre una vista centrale delle azioni. \[S3\]\[S5\]

**Si possono riutilizzare dati da studi precedenti?**

> Sì. Sphera evidenzia il riuso di valutazioni precedenti e le funzioni Copy/AutoType. \[S2\]\[S3\]

**PHA-Pro crea diagrammi?**

> Sono documentati diagrammi collegati ai worksheet; la loro funzione è integrare la vista dello studio e non sostituire i disegni di ingegneria. \[S3\]\[S5\]

**È possibile esportare in Word, Excel e HTML?**

> La brochure ufficiale cita Word, Excel e HTML. I formati disponibili in una specifica installazione vanno verificati. \[S3\]

**Il video fornito è la fonte degli screenshot in questo documento?**

> No. Il video non è stato recuperato; gli screenshot esterni sono identificati con la propria provenienza.

# 22. Glossario

| **Termine**                   | **Definizione**                                                                          |
|-------------------------------|------------------------------------------------------------------------------------------|
| PHA                           | Process Hazard Analysis: analisi strutturata dei pericoli di processo.                   |
| HAZOP                         | Hazard and Operability Study: studio sistematico di deviazioni dall’intento di progetto. |
| HAZID                         | Hazard Identification: identificazione dei pericoli di una facility o attività.          |
| Node                          | Porzione di processo definita come unità di analisi.                                     |
| Guideword                     | Parola guida applicata a un parametro per identificare una deviazione.                   |
| Deviation                     | Scostamento dall’intento di progetto o dalle condizioni attese.                          |
| Cause                         | Meccanismo o evento che genera la deviazione.                                            |
| Consequence                   | Effetto risultante dalla deviazione.                                                     |
| Safeguard                     | Misura preventiva o mitigativa esistente.                                                |
| Risk Ranking                  | Classe di rischio risultante dai criteri configurati.                                    |
| LOPA                          | Layer of Protection Analysis: analisi degli strati indipendenti di protezione.           |
| SIL                           | Safety Integrity Level: livello di integrità di sicurezza.                               |
| AutoType                      | Funzione di inserimento/riuso guidato di valori standardizzati.                          |
| Release Management            | Gestione di approvazioni, versioni e tracciabilità delle modifiche.                      |
| Revalidation                  | Riesame periodico o a seguito di cambiamenti di uno studio o dei suoi elementi.          |
| Criticality Matrix / Heat Map | Matrice visuale di classificazione e distribuzione del rischio.                          |

# 23. Galleria di schermate UI e provenienza

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>COME LEGGERE QUESTA GALLERIA</strong></p>
<p>Le voci seguenti rimandano a screenshot e pagine esterne realmente reperibili. In questa sessione non è stato possibile incorporare i file immagine nel DOCX perché gli host delle immagini non hanno consentito il download diretto; i link aprono la schermata originale o il documento sorgente. Non sono immagini generate o ricostruite.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Figura 1 - HAZOP Study Worksheet Overview

Screenshot esterno della griglia HAZOP. Sono visibili deviazioni, cause, conseguenze, ranking inerente, salvaguardie e raccomandazioni. L’immagine è pubblicata nella scheda prodotto Sphera su Environmental Expert; non è attestato che appartenga alla stessa build del video fornito.

**Immagine originale:** [<u>Apri screenshot / immagine</u>](https://d35rpq4gusjz9h.cloudfront.net/files/96950/products/833693/96950_4_202203111222434772099.jpg) \| Pagina o contesto: [<u>Apri fonte</u>](https://www.environmental-expert.com/software/sphera-version-pha-pro-hazop-process-hazard-analysis-software-833693)

## Figura 2 - HAZOP Heat Map Interface (Sphera)

Immagine ufficiale Sphera con heat map HAZOP: matrice colorata di severità/probabilità e indicatori aggregati. È un’immagine promozionale/documentale, non la prova della UI della versione legacy.

**Immagine originale:** [<u>Apri screenshot / immagine</u>](https://sphera.com/wp-content/uploads/2025/06/PHA-Pro-Header.webp) \| Pagina o contesto: [<u>Apri fonte</u>](https://sphera.com/solutions/process-safety-management/advanced-risk-assessment-software-and-services/process-hazard-analysis-pha-pro-hazop/)

## Figura 3 - PHA-Pro 8.1 HAZOP Worksheet / About

Screenshot pubblico con finestra About che mostra PHA-Pro 8.1.0.0 e il worksheet sottostante. La fonte è un post LinkedIn; utile per confermare la famiglia/versione visualizzata, ma non è una fonte ufficiale del produttore.

**Immagine originale:** [<u>Apri screenshot / immagine</u>](https://media.licdn.com/dms/image/v2/D4D22AQEWoOiDxToCtg/feedshare-shrink_800/B4DZmQmZ0bJAAg-/0/1759067612393?e=2147483647&t=1OohJxIQZFxOAMp2BtNIVer3vcfevE_fnV9wVPszsfA&v=beta) \| Pagina o contesto: [<u>Apri fonte</u>](https://www.linkedin.com/posts/kashif-jameel-csp%C2%AE-nebosh-igc-5ba83a159_processsafety-pha-hazop-activity-7378064328584785921-0_-v)

## Figura 4 - PHA-Pro 8 Administration / Workspace

Il report HAZOP/HAZID di IOCL dichiara espressamente di aver utilizzato PHA PRO by Dyadem e contiene una schermata della UI. Il testo indicizza Workspace, Active Libraries, le schede superiori e i campi amministrativi. Aprire il PDF e cercare “ABOUT THE SOFTWARE” / pagina stampata 3-1 per individuare la schermata.

**Immagine originale:** [<u>Apri screenshot / immagine</u>](https://environmentclearance.nic.in/writereaddata/online/RiskAssessment/231020176U2UDUPXAnnexure-documentofRiskAssessment.pdf) \| Pagina o contesto: [<u>Apri fonte</u>](https://environmentclearance.nic.in/writereaddata/online/RiskAssessment/231020176U2UDUPXAnnexure-documentofRiskAssessment.pdf)

## Figura 5 - HAZOP Worksheet con esempio industriale H2Station

Il report pubblico sul piano di sicurezza H2Station include schermate PHA-Pro con Node, Deviation, Cause, Consequence, risk reduction, Safeguards, Recommendations e Responsibility. Consultare la sezione 5.4.1 (PDF, pagina indicata come 29/30).

**Immagine originale:** [<u>Apri screenshot / immagine</u>](https://h2tools.org/sites/default/files/App2_Consolidated_Safety_Plans.pdf) \| Pagina o contesto: [<u>Apri fonte</u>](https://h2tools.org/sites/default/files/App2_Consolidated_Safety_Plans.pdf)

# 24. Fonti e riferimenti

Le fonti sono elencate con indicazione del tipo e del loro ruolo nella documentazione. Le fonti ufficiali del produttore sono privilegiate per il perimetro funzionale attuale; manuali e training legacy sono usati per descrivere i menu e i workflow desktop; report di progetto e screenshot esterni servono a documentare la UI e casi d’uso reali.

**\[S1\] Video YouTube indicato dall’utente (da 01:21).** [<u>https://www.youtube.com/watch?v=jfCmCVNGgaU&t=81s</u>](https://www.youtube.com/watch?v=jfCmCVNGgaU&t=81s) — Fonte primaria richiesta. Non è stato possibile recuperare pagina, trascrizione o frame in questa sessione; non è usato per attribuire timestamp o schermate.

**\[S2\] Sphera - Process Hazard Analysis (PHA-Pro) & HAZOP.** [<u>https://sphera.com/solutions/process-safety-management/advanced-risk-assessment-software-and-services/process-hazard-analysis-pha-pro-hazop/</u>](https://sphera.com/solutions/process-safety-management/advanced-risk-assessment-software-and-services/process-hazard-analysis-pha-pro-hazop/) — Pagina ufficiale del prodotto; descrizione della soluzione e delle capacità.

**\[S3\] Sphera - PHA-Pro brochure (2025).** [<u>https://sphera.com/wp-content/uploads/2025/08/SPH_ORM_PHA-Brochure-Refresh-FINAL-7.29.2025.pdf</u>](https://sphera.com/wp-content/uploads/2025/08/SPH_ORM_PHA-Brochure-Refresh-FINAL-7.29.2025.pdf) — Fonte ufficiale per metodologie, collegamento diagrammi/worksheet, report, AutoType, Copy, Release Management, Criticality Matrix e Recommendations Manager.

**\[S4\] PHA-Pro 8.3.4 User Guide (2 aprile 2013).** [<u>https://pdfcoffee.com/pha-pro-user-guide-834-5-pdf-free.html</u>](https://pdfcoffee.com/pha-pro-user-guide-834-5-pdf-free.html) — Manuale legacy accessibile tramite mirror di terza parte; utile per dettagli dell’interfaccia desktop e delle impostazioni.

**\[S5\] PHA-Pro 8 End-User Exercises.** [<u>https://www.scribd.com/document/799088175/PHA-Pro-8-End-User-Exercises</u>](https://www.scribd.com/document/799088175/PHA-Pro-8-End-User-Exercises) — Materiale formativo non ufficiale; descrive wizard, Nodes, Deviations, worksheet formatting, risk matrix, report, release management e linked diagram.

**\[S6\] Environmental Expert - Sphera PHA-Pro product listing.** [<u>https://www.environmental-expert.com/software/sphera-version-pha-pro-hazop-process-hazard-analysis-software-833693</u>](https://www.environmental-expert.com/software/sphera-version-pha-pro-hazop-process-hazard-analysis-software-833693) — Pagina con screenshot HAZOP worksheet e descrizione del prodotto.

**\[S7\] LinkedIn - PHA-Pro 8.1 worksheet screenshot.** [<u>https://www.linkedin.com/posts/kashif-jameel-csp%C2%AE-nebosh-igc-5ba83a159_processsafety-pha-hazop-activity-7378064328584785921-0\_-v</u>](https://www.linkedin.com/posts/kashif-jameel-csp%C2%AE-nebosh-igc-5ba83a159_processsafety-pha-hazop-activity-7378064328584785921-0_-v) — Screenshot pubblico di una UI PHA-Pro 8.1; provenienza non ufficiale.

**\[S8\] DEKRA / Chilworth - HAZOP/HAZID Study Report, IOCL Indane Bottling Plant, Pattikalan (2014), Annexure IV.** [<u>https://environmentclearance.nic.in/writereaddata/online/RiskAssessment/231020176U2UDUPXAnnexure-documentofRiskAssessment.pdf</u>](https://environmentclearance.nic.in/writereaddata/online/RiskAssessment/231020176U2UDUPXAnnexure-documentofRiskAssessment.pdf) — Report pubblico di progetto; sezione 3.3 dichiara l’uso di PHA PRO by Dyadem e incorpora una schermata PHA-Pro 8 con Administration e Workspace.

**\[S9\] H2Tools - Consolidated Safety Plans, appendice H2Station.** [<u>https://h2tools.org/sites/default/files/App2_Consolidated_Safety_Plans.pdf</u>](https://h2tools.org/sites/default/files/App2_Consolidated_Safety_Plans.pdf) — Report pubblico con schermate worksheet PHA-Pro e workflow HAZOP/LOPA.

**\[S10\] Sphera - PHA-Pro official header / HAZOP heat map image.** [<u>https://sphera.com/wp-content/uploads/2025/06/PHA-Pro-Header.webp</u>](https://sphera.com/wp-content/uploads/2025/06/PHA-Pro-Header.webp) — Immagine ufficiale di prodotto con heat map HAZOP.

**\[S11\] ProcessEng - Guide to Selecting the Right PHA Documenting Software.** [<u>https://processengr.com/wp-content/uploads/2019/11/pha_documentation_software_selection_guide.pdf</u>](https://processengr.com/wp-content/uploads/2019/11/pha_documentation_software_selection_guide.pdf) — Confronto indipendente che descrive PHA-Pro come sistema di tabbed spreadsheets con colonne modificabili.

**\[S12\] UNECE - Risk Assessment for Industrial Accident Prevention (2024).** [<u>https://unece.org/sites/default/files/2024-11/081124_2325788_E_ECE_CP.TEIA_45_WEB%20%281%29.pdf</u>](https://unece.org/sites/default/files/2024-11/081124_2325788_E_ECE_CP.TEIA_45_WEB%20%281%29.pdf) — Riferimento istituzionale che include PHA-Pro tra gli strumenti per l’analisi dei pericoli di processo.

**\[S13\] EnVizTec - PHA-Pro product page.** [<u>https://www.enviztec.com.au/products/pha-pro/</u>](https://www.enviztec.com.au/products/pha-pro/) — Partner/distributore: informazioni su versione 8 e metodologie supportate.
