# Esercizi di calibrazione

Tutti gli esempi sono sintetici. Puoi adattarli al canale e al destinatario scelti, mantenendo una sola dimensione variabile per confronto.

## Dimensioni

| Gruppo | Dimensione | Domanda implicita |
| --- | --- | --- |
| Struttura | answer-first / context-first | il punto arriva subito o dopo il contesto? |
| Struttura | lunghezza | quanto è lungo un testo "giusto"? |
| Struttura | prosa / elenchi | quando usa un elenco? |
| Struttura | riepilogo finale | chiude riassumendo? |
| Tono | formalità | tu / Lei / voi, registro |
| Tono | calore | quanta cortesia relazionale? |
| Tono | assertività | afferma o suggerisce? |
| Tono | attenuazioni | quante cautele per frase incerta? |
| Tono | disaccordo | come dissente con chi è più senior? |
| Tono | responsabilità | come comunica ritardi ed errori propri? |
| Tono | enfasi | tollera entusiasmo nelle comunicazioni? |
| Lessico | tecnicismi e anglicismi | "deploy" o "rilascio"? |
| Lessico | persona | io / noi / impersonale |
| Lessico | forma verbale nelle procedure | imperativo, infinito, impersonale |
| Lessico | punteggiatura | due punti, punto e virgola, trattini |
| Cornice | aperture | come inizia una mail? |
| Cornice | chiusure | come la chiude? |
| Slide | titoli | argomento o conclusione? |

### Priorità per canale

- **Email interna:** answer-first, lunghezza, prosa/elenchi, aperture, chiusure, tecnicismi.
- **Email superiore:** answer-first, assertività, attenuazioni, disaccordo, responsabilità.
- **Email cliente:** formalità, calore, responsabilità, enfasi, chiusure.
- **Documentazione:** forma verbale, persona, tecnicismi, prosa/elenchi.
- **Slide:** titoli, lunghezza, enfasi, tecnicismi.

## Domande di contesto (percorso A)

Una per messaggio:

1. Quale tipo di testo ti crea più problemi oggi: mail interne, mail a superiori, mail a clienti, documentazione o slide?
2. A chi scrivi più spesso?
3. Cosa deve fare di solito chi legge: decidere, rispondere, eseguire, essere informato?
4. Hai ricevuto commenti sui testi prodotti con Claude? Quali?
5. C'è qualcosa che correggi sempre nelle bozze di Claude?

## Confronti A/B

Formato della domanda: "Quale invieresti più facilmente? Rispondi A, B, nessuna, oppure riscrivila." La dimensione tra parentesi è per te: non mostrarla prima della risposta.

1. (answer-first — email superiore)
   - A. Ciao Laura, ieri abbiamo completato i test di carico in collaudo. Sono emersi tempi di risposta oltre soglia sul servizio di export, quindi il rilascio di venerdì non è confermabile.
   - B. Ciao Laura, il rilascio di venerdì non è confermabile: i test di carico di ieri in collaudo hanno mostrato tempi di risposta oltre soglia sul servizio di export.
2. (assertività — email interna)
   - A. Ti segnalo che, alla luce delle verifiche effettuate, potrebbe essere utile rivedere la stima.
   - B. Le verifiche mostrano che la stima va rivista.
3. (attenuazioni — email interna)
   - A. Il problema potrebbe forse dipendere dalla configurazione del pool di connessioni.
   - B. Il problema dipende probabilmente dalla configurazione del pool di connessioni.
4. (prosa / elenchi — email interna)
   - A. Per procedere mi servono le credenziali dell'ambiente di test e la conferma della versione del driver.
   - B. Per procedere mi servono:
     - le credenziali dell'ambiente di test;
     - la conferma della versione del driver.
5. (formalità — email cliente)
   - A. Le confermo che il rilascio avverrà giovedì.
   - B. Ti confermo che il rilascio avverrà giovedì.
6. (aperture — email interna)
   - A. Ciao Marco, spero tutto bene. Ti scrivo per chiederti l'accesso al repository di integrazione.
   - B. Ciao Marco, mi serve l'accesso al repository di integrazione.
7. (chiusure — email interna)
   - A. … Fammi sapere se ti serve altro. Grazie mille e buona giornata!
   - B. … Grazie.
8. (riepilogo finale — email superiore, mail di 3 paragrafi)
   - A. Chiude con: "In sintesi: rilascio spostato a martedì, nessun impatto sul collaudo utente."
   - B. Chiude senza riepilogo.
9. (responsabilità — email cliente)
   - A. La consegna subirà uno slittamento a martedì 14 a causa di un'errata stima dell'integrazione.
   - B. Abbiamo stimato male l'integrazione: la consegna slitta a martedì 14.
10. (disaccordo — email a un senior)
    - A. Capisco l'approccio, ma temo che la cache condivisa possa creare qualche problema di consistenza.
    - B. La cache condivisa crea un rischio di consistenza: per alcuni minuti due istanze possono restituire dati diversi.
11. (tecnicismi — email interna)
    - A. Facciamo il deploy della fix in staging e poi apriamo la PR.
    - B. Rilasciamo la correzione in collaudo e poi apriamo la richiesta di merge.
12. (enfasi — comunicazione di rilascio a cliente)
    - A. Siamo lieti di annunciarvi che da lunedì è disponibile la versione 3.2, ricca di nuove funzionalità!
    - B. Vi informiamo che da lunedì è disponibile la versione 3.2, con alcune nuove funzionalità.
13. (forma verbale — documentazione)
    - A. Fermare il servizio ed eseguire lo script di migrazione.
    - B. Ferma il servizio ed esegui lo script di migrazione.
14. (titoli — slide management)
    - A. Stato del progetto
    - B. Il progetto è in linea, con un rischio sui tempi di collaudo

## Micro-scritture

"Scrivi una o due frasi, come le scriveresti davvero." Non correggere grammatica o stile: estrai i segnali, poi chiedi se eventuali irregolarità sono volute.

1. Comunichi a un superiore un ritardo di una settimana, senza scaricare colpe.
2. Dissenti da una soluzione tecnica proposta da un collega più senior.
3. Chiedi a un responsabile di decidere tra due opzioni entro venerdì.
4. Aggiorni un cliente su un rischio che potrebbe spostare il collaudo.
5. Annunci a un cliente un nuovo rilascio con due novità che lo riguardano.
6. Scrivi il titolo di una slide che dice la conclusione: costi in linea, tempi a rischio.
7. Introduci in una frase una procedura tecnica di installazione.

## Anti-esempi

Mostra 3–4 varianti della stessa frase e chiedi: "Quale non scriveresti mai, e perché?" Il motivo vale più della scelta: va in "Da evitare".

Categorie da coprire nel tempo: entusiasmo ingiustificato, corporate speak, eccesso di cautela, assertività aggressiva, dettagli inutili, riepiloghi ridondanti, richiesta nascosta in fondo, titoli di slide generici.

Esempio (richiesta a collega):

- A. Quando hai un attimo, riusciresti a darmi una mano con l'accesso al repository? Nessuna urgenza!
- B. Mi serve l'accesso al repository entro domani per completare il rilascio.
- C. È fondamentale ricevere l'accesso al repository al fine di garantire il rispetto delle tempistiche.
- D. Accesso al repository: mi serve entro domani.
