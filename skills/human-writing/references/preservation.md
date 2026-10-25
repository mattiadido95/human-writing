# Preservazione

Nessuna preferenza di stile giustifica una modifica di contenuto. Se una regola di stile confligge con la precisione, vince la precisione.

## Mai modificare

- Nomi di persone, aziende, prodotti, sistemi, componenti.
- Numeri, importi, percentuali, unità di misura, versioni.
- Date, orari, scadenze, durate.
- URL, path, nomi di file, codici di ticket, identificativi.
- Citazioni testuali.
- Termini tecnici con significato preciso e sigle. Non sostituirli con sinonimi.
- Richieste, decisioni attese, scadenze e destinatari dell'azione.
- Negazioni e condizioni ("solo se", "salvo", "a meno che").

## Grado di certezza

Mantieni lo stesso livello. Esempi di alterazioni critiche:

- "probabilmente dipende da X" → "dipende da X";
- "dovremmo rilasciare giovedì" → "rilasceremo giovedì";
- "non abbiamo ancora verificato" → omesso;
- "stima preliminare" → "stima".

È lecito ridurre le catene di attenuazioni ("potrebbe forse essere utile valutare" → "conviene valutare") solo se il grado di certezza resta lo stesso.

## Mai aggiungere

- fatti, numeri, nomi, date;
- motivazioni o cause non dichiarate;
- promesse, impegni, scadenze;
- scuse o ammissioni di responsabilità non presenti;
- attribuzioni di colpa;
- dettagli inventati per rendere il testo più concreto.

## Struttura da preservare nei file

Blocchi di codice e codice inline, frontmatter, target dei link e ancore, tabelle di dati, segnaposto e variabili (`{nome}`, `${VAR}`, `[DA COMPLETARE]`), commenti tecnici.

## Cosa si può cambiare

Ordine delle frasi, divisione o unione di frasi, connettivi, lessico non tecnico, rimozione di ridondanze e formule vuote, purché non si perda informazione.

## Documentazione

- Le ripetizioni necessarie in una procedura restano: ogni passo deve essere eseguibile da solo.
- Avvertenze, prerequisiti e limiti non si accorciano fino a perderne il senso.

## Verifica

Prima di restituire, elenca mentalmente i fatti dell'input (persone, numeri, date, impegni, livello di certezza) e controlla che ciascuno sia nell'output, invariato. Controlla anche il contrario: nell'output non ci sono fatti assenti dall'input.
