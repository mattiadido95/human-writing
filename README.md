# Human Writing

[English](README.en.md)

Due skill complementari per Claude Code: una scrive e revisiona testi destinati a persone, l'altra costruisce un profilo di scrittura personale attraverso esercizi e correzioni approvate dall'utente.

## Cos'è una skill

Una skill è una cartella con un file `SKILL.md` e, quando servono, materiali di riferimento. Fornisce a Claude Code istruzioni riutilizzabili per un compito specifico. Questo repository contiene istruzioni Markdown: non è un'applicazione, non richiede librerie aggiuntive e non modifica il modello.

Per il funzionamento delle skill e le directory supportate, consulta la [documentazione ufficiale di Claude](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview).

## Le due skill

| Skill | Scopo | Attivazione |
| --- | --- | --- |
| `human-writing` | Scrivere, riscrivere o analizzare testi applicando il profilo personale e riducendo formule artificiali o ripetitive. | Su richiesta pertinente oppure con `/human-writing`. |
| `writing-calibrator` | Costruire e aggiornare il profilo attraverso domande, confronti A/B, brevi scritture e confronto tra bozza e testo finale. | Solo con invocazione esplicita: `/writing-calibrator`. |

I testi coperti sono email a colleghi, superiori e clienti, documentazione tecnica e progettuale e testi per presentazioni. Il registro cambia in base al canale e al destinatario.

`human-writing` distingue tre modalità:

- `generate`: crea un testo dai fatti forniti, usando segnaposto per i dati necessari che mancano;
- `rewrite`: interviene il minimo necessario su un testo esistente;
- `audit`: segnala problemi e direzioni di correzione senza riscrivere il testo.

La precisione prevale sulle preferenze di stile: fatti, numeri, date, citazioni, termini tecnici e grado di certezza devono essere preservati. L'obiettivo è una scrittura naturale e adatta al lettore, senza errori simulati o ottimizzazioni contro gli AI detector.

## Struttura

```text
skills/
  human-writing/
    SKILL.md
    references/
      preservation.md
      channels.md
      ai-patterns.md
  writing-calibrator/
    SKILL.md
    references/
      exercises.md
      evidence-and-privacy.md
```

## Installazione in Claude Code

Prerequisito: Claude Code con supporto alle skill locali.

Copia le due cartelle contenute in `skills/` nella directory delle skill personali o del progetto, mantenendole affiancate. Non copiare l'intero repository come un'unica skill.

| Ambito | Directory delle skill | Directory del profilo |
| --- | --- | --- |
| Personale | `~/.claude/skills/` | `~/.claude/writing-profile/` |
| Progetto | `<progetto>/.claude/skills/` | `<progetto>/.claude/writing-profile/` |

La struttura risultante, nell'installazione personale, è:

```text
~/.claude/
  skills/
    human-writing/
      SKILL.md
      references/
    writing-calibrator/
      SKILL.md
      references/
  writing-profile/
    voice-profile.md
    evidence-log.md
```

Le due skill devono stare nella stessa directory `skills/`: il calibratore legge anche i pattern di `human-writing`. I percorsi del profilo sono relativi alla cartella di ogni skill (`../../writing-profile/`).

### Profilo e registro: configurazione separata

Questo repository non include `voice-profile.md`, `evidence-log.md` o template per inizializzarli. Non contiene un profilo personale già calibrato.

- `voice-profile.md` contiene le preferenze approvate, organizzate per ambito, con stato e regole provvisorie o confermate.
- `evidence-log.md` contiene evidenze, ipotesi, contraddizioni, changelog e stato della calibrazione.

Se il profilo manca, è malformato o ha `status: vuoto`, `human-writing` può usare le regole generali e suggerisce il calibratore. Se profilo o registro mancano o sono malformati, `writing-calibrator` si ferma e chiede come procedere: non li inizializza né li sovrascrive automaticamente. La prima configurazione di questi file è quindi un passaggio separato da concordare con l'agente.

I file personali devono restare fuori dal repository pubblico. Nell'installazione di progetto, escludi `.claude/writing-profile/` dal relativo controllo di versione. Il `.gitignore` di questo repository esclude la directory `writing-profile/`.

## Esempi d'uso

```text
/human-writing Scrivi una mail a un collega: mi serve la conferma della versione del driver entro venerdì per procedere con il collaudo.
```

```text
/human-writing Riscrivi questa mail per un cliente, mantenendo invariati fatti e scadenze: [testo]
```

```text
/human-writing Controlla il tono di questo testo senza riscriverlo: [testo]
```

Con profilo e registro predisposti:

```text
/writing-calibrator mail cliente
```

```text
/writing-calibrator Confronta questa bozza con il testo che ho effettivamente inviato: [bozza e testo finale anonimizzati]
```

Il calibratore fa una domanda alla volta. Una singola risposta è un'evidenza, non una regola confermata; le modifiche al profilo richiedono approvazione esplicita. `human-writing` legge il profilo, ma non lo aggiorna.

## Lingue e limiti

- Le istruzioni sono in italiano e il primo percorso di calibrazione copre solo l'italiano. Il README in inglese documenta lo stesso comportamento: non estende la calibrazione all'inglese.
- Per testi inglesi, `human-writing` applica preservazione, regole di canale e pattern generici, senza tradurre automaticamente le preferenze italiane.
- Le presentazioni sono coperte solo per il testo: queste skill non generano layout o file `.pptx`.
- Codice, SQL, JSON, configurazioni, commit message, stack trace, commenti nel codice e risposte tecniche in chat sono fuori ambito.
- I testi prodotti vanno riletti prima dell'invio; il controllo finale previsto dalla skill non garantisce l'assenza di errori.

## Privacy

Gli esercizi forniti sono sintetici. Il calibratore richiede esempi anonimizzati e non conserva testi completi. Le regole di riferimento escludono credenziali, dati regolati e materiale cliente o confidenziale dalla calibrazione; il salvataggio delle evidenze richiede consenso.

L'elaborazione dei testi avviene nell'ambiente Claude Code utilizzato: queste istruzioni non introducono un servizio di elaborazione locale né cambiano le condizioni di trattamento dei dati del servizio.
