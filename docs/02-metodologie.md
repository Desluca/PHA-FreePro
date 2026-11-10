# 02 — Metodologie supportate

Ogni metodologia è un **template**: una gerarchia di livelli, un insieme di fogli e colonne, liste di valori e regole di calcolo (vedi [04-modello-dati.md](04-modello-dati.md)). Questo documento descrive *cosa* deve fare ciascun template di serie e *come* il programma lo supporta.

Riferimenti normativi: IEC 61882:2016 (HAZOP), CCPS *Layer of Protection Analysis* (2001) e *Guidelines for Initiating Events and IPLs* (2015), IEC 61511 (SIS), IEC 60812 (FMEA), ISO 31000.

---

<a id="hazop"></a>
## 1. HAZOP — Hazard and Operability Study

### Concetto
Si divide l'impianto in **nodi** (sezioni con un intento progettuale definito). A ogni nodo si applicano **guideword** a **parametri** di processo, ottenendo **deviazioni** (es. *NO* + *Flusso* = "Nessun flusso"). Per ogni deviazione il team cerca cause credibili, conseguenze, salvaguardie e valuta il rischio.

### Gerarchia del template HAZOP

```
Studio
 └─ Nodo                  (es. "N-01 Linea alimentazione da serbatoio T-101 a pompa P-101 A/B")
     └─ Deviazione        (guideword + parametro, es. "Più pressione")
         └─ Causa         (es. "Valvola di blocco a valle chiusa per errore")
             └─ Conseguenza   (es. "Sovrapressione linea, rottura flangia, rilascio di infiammabile")
                 ├─ Salvaguardie   (N per conseguenza, es. "PSV-101 tarata a 10 barg")
                 ├─ Rischio        (S, L, R iniziali — S, L, R residui)
                 └─ Raccomandazioni (N, collegate al Recommendations Manager)
```

### Colonne del foglio HAZOP (template di serie)

| Colonna | Tipo | Note |
|---|---|---|
| Nodo | riferimento | Con descrizione, **tipo** (linea, recipiente, scambiatore, pompa…), intento progettuale, condizioni operative (P, T, portata), disegni collegati. Si può riusare da studi precedenti |
| Guideword | lista | NO/NON, PIÙ, MENO, ANCHE, PARTE DI, INVERSO, ALTRO DA, PRIMA, DOPO, PRESTO, TARDI |
| Parametro | lista | Flusso, Pressione, Temperatura, Livello, Composizione, Fase, Reazione, Viscosità, Tempo, Sequenza, Manutenzione, Avviamento/Arresto, Utilities, Campionamento, Corrosione/Erosione, Sicurezza servizi… |
| Deviazione | testo calcolato/editabile | Default = guideword + parametro |
| Causa | testo + AutoType + libreria | Opzionale: **frequenza della causa** (per la LOPA) e categoria (guasto apparecchiatura, errore umano, esterno) |
| Conseguenza | testo | |
| Categoria conseguenza | lista | Persone/sicurezza, ambiente, asset, produzione, reputazione (codici dal Data Dictionary); può selezionare il risk system da usare |
| Salvaguardie | lista multi-riga | Tag strumento, tipo (BPCS, allarme+operatore, PSV, SIS, fisica), flag "candidato IPL" |
| S | lista | Severità secondo la matrice |
| L | lista | Probabilità (Likelihood) |
| R | calcolato | Da matrice S×L; colorato |
| Raccomandazioni | link | Rimando a una o più raccomandazioni (anche condivise fra righe) |
| S residua / L residua / R residuo | lista/calcolato | Dopo l'attuazione delle raccomandazioni |
| Commenti | testo | Note del team, "parking lot" |
| Riferimenti | link | Disegni, documenti, incidenti storici |
| Stato | lista | Da discutere / Discussa / Non applicabile ("No credible causes") |

### Funzioni specifiche HAZOP

- **Generazione deviazioni**: selezionando un nodo si propone la matrice guideword×parametro; l'utente spunta le combinazioni rilevanti e il programma crea le righe.
- **Nessuna causa credibile**: una deviazione può essere chiusa come "non credibile" con una motivazione; resta nel report come prova che è stata considerata.
- **Riferimento incrociato**: una causa che si propaga a un altro nodo ("vedi Nodo 3, Più pressione") diventa un link navigabile.
- **Copia nodo**: per treni paralleli (pompa A/B, linee gemelle) si duplica un nodo con tutte le righe, oppure lo si **collega** (mirroring: modifiche nel nodo master si propagano).

---

<a id="whatif"></a>
## 2. What-If

Brainstorming strutturato con domande "Cosa succede se…?". Gerarchia: **Sistema/Area → Domanda What-If → Conseguenza → Salvaguardie → Rischio → Raccomandazioni**. Le domande possono arrivare dalla libreria per categoria (errore operatore, guasto utilities, eventi esterni, manutenzione). Spesso si usa insieme alla checklist (**What-If/Checklist**).

<a id="checklist"></a>
## 3. Checklist

Verifica di conformità a buone pratiche. Gerarchia: **Area/Categoria → Voce di checklist → Risposta (Sì/No/N.A./Parziale) → Commento → Raccomandazione**. La libreria di serie punta a **≥ 2.500 voci** (come il prodotto di riferimento), organizzate per apparecchiatura (compressori, scambiatori, serbatoi, forni, tubazioni, sistemi di sicurezza, edifici, elettrico, antincendio, fattori umani, gestione delle modifiche…). Le voci vanno **scritte da zero** dal progetto o prese da fonti pubbliche (es. checklist OSHA/CCPS di dominio pubblico) — non dalle librerie Sphera.

<a id="fmea"></a>
## 4. FMEA / FMECA

Per apparecchiature o sistemi meccanici. Gerarchia: **Sistema → Componente → Funzione → Modo di guasto → Effetto (locale/sistema) → Causa → Controlli → S/O/D → RPN → Azioni**. Il calcolo **RPN = S × O × D** (scale 1–10) o, in alternativa, l'**Action Priority** di AIAG-VDA. Template opzionale di fase 3.

<a id="hazid"></a>
## 5. HAZID / PHA preliminare

Identificazione pericoli in fase di concept. Gerarchia: **Area → Categoria di pericolo (da libreria) → Pericolo → Causa → Conseguenza → Salvaguardie → Rischio → Azioni**.

---

<a id="matrice"></a>
## 6. Matrice di rischio (Criticality Matrix)

- Dimensione configurabile (da 3×3 a 7×7); assi **Severità** (righe) e **Probabilità** (colonne), oppure invertiti.
- Ogni livello di severità ha una descrizione per **categoria di impatto** (Persone, Ambiente, Asset/Economico, Reputazione). Si sceglie il livello peggiore fra le categorie, oppure si valuta il rischio per categoria (più valutazioni sulla stessa riga).
- Ogni livello di probabilità ha una **frequenza** (eventi/anno) usata dalla LOPA per derivare la frequenza tollerabile.
- Ogni cella ha: **valore/etichetta** (es. 1–25, o A/B/C/D), **colore**, **classe di rischio** (Inaccettabile / ALARP / Accettabile), **azione richiesta** (es. "raccomandazione obbligatoria entro 30 giorni").
- **Rischio iniziale** (solo salvaguardie esistenti) e **residuo** (dopo le raccomandazioni).
- Le matrici sono a livello di **organizzazione** e copiate nello studio al momento della creazione (la modifica della matrice aziendale non altera gli studi chiusi).
- Report: **heat map** con numero di scenari per cella, prima e dopo.

---

<a id="lopa"></a>
## 7. LOPA — Layer of Protection Analysis

### Concetto
Analisi semi-quantitativa di uno **scenario** (causa → conseguenza) per verificare se le **protezioni indipendenti (IPL)** riducono la frequenza dell'evento sotto il **target tollerabile**. Se non basta, si individua il gap e il **SIL** della funzione strumentata di sicurezza (SIF) necessaria.

### Collegamento HAZOP → LOPA
- Le righe HAZOP con rischio ≥ soglia configurata (o selezionate a mano) generano uno **scenario LOPA collegato**.
- Causa, conseguenza, severità e salvaguardie sono **mirrorate** (non copiate): se cambiano nell'HAZOP, la LOPA mostra l'aggiornamento e segnala che lo scenario va ricontrollato.
- Le salvaguardie marcate "candidato IPL" compaiono già come IPL da validare.

### Colonne del foglio LOPA

| Colonna | Tipo | Formula / note |
|---|---|---|
| ID scenario | auto | Link alla riga HAZOP di origine |
| Descrizione conseguenza | mirror | Da HAZOP |
| Severità | mirror/lista | Determina la **frequenza target** (TMEL, Target Mitigated Event Likelihood) |
| Frequenza target | calcolato | Da tabella severità → frequenza (configurabile) |
| Evento iniziatore (IE) | mirror | La causa |
| Frequenza IE | numero | Da libreria IE (es. guasto loop BPCS = 1E-1/anno) |
| Modificatori abilitanti | numeri | Probabilità di presenza (time at risk), probabilità di accensione, probabilità di presenza persone, probabilità di lesione mortale — ciascuno ≤ 1 |
| IPL 1…n | righe | Descrizione, tipo, **PFD** (da libreria: es. PSV = 1E-2, allarme + risposta operatore = 1E-1, BPCS = 1E-1), check di indipendenza/auditabilità/efficacia |
| Frequenza mitigata | calcolato | `MEF = f_IE × Π(modificatori) × Π(PFD_IPL)` |
| Rapporto / gap | calcolato | `RRF richiesto = MEF / TMEL` |
| SIL richiesto | calcolato | Da RRF: 10–100 → SIL 1, 100–1.000 → SIL 2, 1.000–10.000 → SIL 3, >10.000 → SIL 4 / riprogettare |
| Esito | calcolato | "Target raggiunto" / "Gap — raccomandazione necessaria" |
| Raccomandazioni | link | Al Recommendations Manager |

### Regole di validazione
- Un IPL deve essere **indipendente** dall'evento iniziatore e dagli altri IPL (es. lo stesso BPCS non può essere sia causa sia IPL; massimo un IPL BPCS per scenario, configurabile).
- Le PFD non possono essere < al valore minimo ammesso per tipo (configurabile).
- Avviso se si mescolano allarmi e operatore come due IPL distinti senza giustificazione.
- Lo scenario mostra la "catena" grafica IE → modificatori → IPL → conseguenza con le frequenze intermedie.

### SIL
Il SIL si determina con tre metodi, ognuno con il proprio template (relazione §2 e §11; brochure Sphera 2025):
- **dalla LOPA** (sopra);
- **Risk Graph** (IEC 61508-5 / IEC 61511-3, allegato D): albero a parametri C (conseguenza), F (esposizione), P (possibilità di evitare), W (probabilità di domanda) → SIL richiesto. Il grafo si calibra nelle impostazioni;
- **Safety Layer Matrix**: matrice severità × probabilità × numero di strati di protezione non-SIS già presenti → SIL richiesto.

Lista di tutte le SIF emerse, con SIL target, scenari che le richiedono (una SIF può proteggere più scenari: vale il SIL più alto), tag strumenti e stato. Esportabile come base per la **Safety Requirements Specification** (IEC 61511).

---

<a id="altri"></a>
## 8-bis. Altri metodi specialistici (fase 4, come template)

Il prodotto di riferimento li elenca nella brochure (relazione §11). Per noi sono template sul motore generico, senza codice dedicato:

| Metodo | Gerarchia del template |
|---|---|
| **CHAZOP** (Computer/Control HAZOP) | Sistema di controllo → Nodo/funzione (I/O, rete, HMI, alimentazione) → Guideword per sistemi digitali → Causa → Conseguenza → Salvaguardie → Rischio |
| **HACCP** | Fase di processo → Pericolo (biologico/chimico/fisico) → Punto critico di controllo (albero decisionale) → Limiti critici → Monitoraggio → Azioni correttive → Verifica |
| **DHA** — Dust Hazard Analysis (NFPA 652) | Area/apparecchiatura → Polvere combustibile (Kst, MIE) → Pericolo (deflagrazione, flash fire) → Fonti di innesco → Salvaguardie → Gap rispetto alla norma |
| **SIMOPS** | Attività A × Attività B (matrice) → Interazione → Pericolo → Controlli → Permesso/restrizione |
| **Security Assessment** (SVA) | Asset → Minaccia → Vulnerabilità → Conseguenza → Contromisure → Rischio |

Il campo **categoria di conseguenza** (persone/sicurezza, ambiente, asset, produzione, reputazione) è comune a tutti i template di valutazione del rischio e alimenta più risk system (M8).

<a id="bowtie"></a>
## 8. Bow-tie (opzionale, fase 4)

Vista grafica derivata dai dati già esistenti, senza reinserimento:
- **Top event** = deviazione o perdita di contenimento;
- **Minacce** a sinistra = cause, con **barriere preventive** = salvaguardie/IPL lato causa;
- **Conseguenze** a destra, con **barriere di mitigazione**;
- **Fattori di escalation** opzionali.

Export SVG/PNG e in un formato di interscambio aperto (JSON). Il prodotto di riferimento sembra ottenere il bow-tie esportando verso un tool esterno; per noi è un valore aggiunto, non un requisito di parità.
