---
name: human-writing
description: Scrive, riscrive o revisiona testi destinati a persone (email a colleghi, superiori o clienti; documentazione tecnica e progettuale; testi per slide) applicando il profilo di scrittura personale dell'utente ed eliminando i tratti tipici della prosa generata da AI. Usare quando l'utente chiede di scrivere, preparare, riscrivere, sistemare, rendere meno artificiale o controllare nel tono una mail, un documento o una presentazione. Non usare per codice, query SQL, JSON, file di configurazione, commit message, stack trace, commenti nel codice o risposte tecniche in chat.
argument-hint: "[richiesta o testo da riscrivere]"
---

# Human writing

Produci testi che l'utente possa inviare come propri: precisi, adatti a chi legge, senza i tratti meccanici della prosa generata. Non introdurre errori, slang o irregolarità simulate. Non ottimizzare contro AI detector.

## 1. Inquadra la richiesta

- **Modalità**
  - `generate`: testo nuovo a partire da fatti, scopo e destinatario;
  - `rewrite`: migliori un testo esistente ("sistemala", "riscrivila", "rendila meno artificiale");
  - `audit`: analizzi senza modificare ("controlla", "cosa non va").
- **Brief interno**, da non mostrare: lingua, canale, destinatario, scopo, cosa deve fare chi legge.
- Chiedi solo se manca un'informazione che cambia materialmente il testo, per esempio il destinatario di una comunicazione delicata. Una domanda sola. Altrimenti procedi.

## 2. Carica

| File | Quando |
| --- | --- |
| `${CLAUDE_SKILL_DIR}/../../writing-profile/voice-profile.md` | sempre |
| `${CLAUDE_SKILL_DIR}/references/preservation.md` | sempre |
| `${CLAUDE_SKILL_DIR}/references/channels.md` | sempre, leggi solo la sezione del canale |
| `${CLAUDE_SKILL_DIR}/references/ai-patterns.md` | sempre in `rewrite` e `audit`; in `generate` per il controllo finale |

Profilo:

- Applica le regole il cui ambito comprende il testo. A parità di conflitto vince l'ambito più specifico: destinatario → canale → lingua → globale.
- `confermata` = regola; `provvisoria` = preferenza da seguire se non confligge con altro.
- "Formule che uso" e "Da evitare" prevalgono su `ai-patterns.md`.
- Profilo assente, malformato o `status: vuoto`: usa solo le reference, poi aggiungi in fondo una riga che suggerisce `/writing-calibrator`. Non bloccare il task.
- Testo in inglese: il profilo copre solo l'italiano. Usa preservazione, canali e pattern generici, non tradurre le preferenze italiane, e segnalalo in una riga.
- Non modificare mai profilo o registro: lo fa solo `/writing-calibrator`.

## 3. Precedenza

1. Policy aziendali e istruzioni esplicite dell'utente.
2. Fatti, fonti, citazioni, grado di certezza (`preservation.md`).
3. Vincoli di canale e destinatario (`channels.md` → Vincoli).
4. Voice profile.
5. Default di canale (`channels.md` → Default).
6. Pattern AI generici (`ai-patterns.md`).

## 4. Esegui

**`generate`**
- Usa solo i fatti forniti.
- Se manca un dato necessario e non l'hai chiesto, inserisci un segnaposto `[DA COMPLETARE: …]`. Non inventare.

**`rewrite`**
- Minimo intervento efficace. Le frasi già naturali restano com'erano.
- Se il testo va già bene, dillo e proponi al massimo ritocchi minimi.
- Modifica solo la prosa che l'utente ti ha chiesto di modificare.
- Su un file: modifica il file solo se richiesto. Codice, frontmatter, link e tabelle di dati restano intatti.

**`audit`**
- Per ogni problema: estratto breve, pattern, effetto su chi legge, direzione di correzione.
- Nessun giudizio sulla paternità AI, nessun punteggio, nessuna modifica.
- Se non ci sono problemi, dillo.

## 5. Controllo finale

Prima di restituire, verifica:

1. Fatti, nomi, numeri, date, citazioni e grado di certezza sono invariati?
2. Hai aggiunto dettagli, promesse o motivazioni non forniti?
3. Il punto principale e l'eventuale richiesta sono riconoscibili subito?
4. Registro e formato sono adatti a destinatario e canale?
5. Hai applicato le regole del profilo pertinenti?
6. Ogni frase aggiunge informazione o una transizione necessaria?
7. Hai tolto tratti autentici dell'autore o formule elencate in "Formule che uso"?
8. Serviva davvero intervenire così tanto?

## 6. Output

- **Email:** oggetto (se pertinente) e corpo, in un blocco ```text così si copia senza formattazione.
- **Slide:** per ogni slide titolo, corpo ed eventuali note, in un blocco ```text.
- **Documentazione:** nel formato del documento di destinazione.
- **`audit`:** elenco dei problemi.
- Niente preamboli ("Ecco la mail") e niente offerte finali, con una sola eccezione: se in questa conversazione l'utente ha chiesto due o più correzioni di stile sullo stesso testo, dopo la versione finale aggiungi una volta la riga «Hai corretto più volte questo testo: `/writing-calibrator` per salvare le correzioni nel profilo.» Le correzioni di fatti non contano. Non salvare nulla tu.
- Dopo il testo, una riga solo se servono: segnaposto da completare, assunzioni fatte, profilo vuoto, lingua non calibrata.
- Spiegazioni o elenco delle modifiche solo se l'utente li chiede.
