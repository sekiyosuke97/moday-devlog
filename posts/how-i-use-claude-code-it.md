<!-- canonical: https://moday.me/blogs/journal/how-i-use-claude-code -->

# Come uso Claude Code — non organizzo, delego, vado a sensazione

## Mi fermo un attimo e metto per iscritto come uso Claude Code

Fin qui ho raccontato la costruzione di MODAY, ma **come piloto Claude Code** non l'ho mai scritto.

La scelta dello stack, la pipeline di distribuzione, la localizzazione in nove lingue, il chatbot tirato su in quindici minuti: tutto stava dal lato del «cosa ho costruito».

Adesso che il negozio è aperto e siamo entrati in fase operativa, è il momento di scriverlo da una prospettiva meta. La conclusione la metto subito: **non organizzo, delego, vado a sensazione**.

Probabilmente è il contrario di quello che si legge in giro sui tutorial di Claude Code.

## Il CLAUDE.md l'ha scritto Claude

Il consiglio comune è: **«mettete in ordine le informazioni del progetto dentro CLAUDE.md»**. Brand, stack tecnico, convenzioni di codice, priorità. L'umano organizza tutto per dare contesto a Claude Code. È l'uso standard.

Il CLAUDE.md di MODAY **non contiene una sola riga scritta da me**. Non so nemmeno cosa ci sia dentro.

All'inizio della costruzione ho detto a Claude Code: «sistemati pure i file da solo». E ha cominciato a mettere ordine — brand, stack, tabella SKU, configurazione dei Markets, priorità per fase. Quando ogni tanto ci do un'occhiata, sembra messo giù in una forma probabilmente più leggibile per Claude di quanto avrei fatto io a mano.

Dall'inizio alla fine, di «organizzare» non ne ho fatto un grammo. **Il lavoro di organizzazione, in sé, l'ho passato a Claude.**

## Le sessioni le divido «a sensazione»

Le sessioni le separo, sì — ma **non ho regole**.

Niente divisione rigorosa per obiettivo: vado per blocchi grossolani tipo «creazione contenuti», «UI/UX», «MD (varie ed eventuali)». Dentro la stessa sessione mischio generazione immagini, traduzione, scrittura di codice.

Non divido per ruolo del tipo «sessione traduzione» / «sessione codice». **Divido per flusso di lavoro.** È un criterio sciatto, ma il risultato è uno stato in cui **le idee si concatenano**.

Sto sistemando l'UI e all'improvviso mi accorgo: «ah, conviene cambiare anche la traduzione in linea con questo». Lancio subito la traduzione, nella stessa sessione. Siccome non c'è alcun costo nel portare il contesto da una sessione all'altra, **il filo del ragionamento non si spezza**. Questo, sorprendentemente, fa la differenza.

## Indicazioni tecniche, quasi mai

L'ho già scritto altrove, ma in fase di scelta dello stack non ho dato nemmeno una condizione tecnica. Tutto quello che ho messo sul tavolo erano vincoli di business. Anche entrato in implementazione, l'atteggiamento non è cambiato.

L'unica cosa che mi assicuro di trasmettere è: **«usa Shopify e Gelato nel modo standard, implementazioni originali al minimo»**.

Lo considero una regola d'oro del SaaS. Stare dentro il perimetro previsto dal vendor è ciò che, sul lungo periodo, regge di più. Le customizzazioni sono attraenti nell'immediato, ma si rompono al primo aggiornamento del vendor. Flussi standard, API standard, struttura di tema standard. Se ne esci, ne esci solo quando è davvero necessario.

Solo trasmettendo questo, posso delegare praticamente tutto a Claude Code: il modo di chiamare le API, la strategia di test, l'error handling, i dettagli implementativi.

## Se mi chiede «mi spieghi questo?», rispondo «fallo tu»

Claude Code ogni tanto chiede conferma. «Posso vedere il contenuto di questo file?», «Va bene così?», «Come scrivo i test?».

A praticamente tutte queste richieste rispondo: **«fallo tu»**.

Se vuoi vedere un file, apri tu il view. Se chiedi una decisione, ti rispondo «decidi tu». Risultato: nella maggior parte dei casi va a leggere da solo, decide da solo, e arriva fino all'implementazione.

È la messa in pratica di quel «**voglio passare l'iniziativa al lato AI**» di cui ho scritto in un altro post. Non restituisco decisioni, lascio che le tenga lui.

Quello che resta in capo a me è solo **il territorio che non si può muovere via API**. Conto in banca, screening dei pagamenti, iscrizioni ai vari servizi, registrazione fatturazione, generazione di API key. Lì il contratto è con una persona fisica, quindi muovo le mani io. Per tutto il resto, la palla ce l'ha Claude.

## Faccio fare il giro di GA4 tutti i giorni, e proporre miglioramenti

Questa è una pratica nuova, partita dopo l'apertura.

Ogni giorno faccio fare a Claude Code il giro di GA4, **e gli faccio tirare fuori criticità e proposte di miglioramento**. Io le guardo e scarto solo quelle palesemente con un'angolazione sbagliata. Il 60–70% che resta lo faccio implementare sul momento.

Tra la proposta e l'implementazione, l'unica cosa che faccio è dire OK/NO. Codice scritto da me: praticamente zero. Design pensato da me: praticamente zero.

Voglio farne un concetto operativo: **«almeno un miglioramento implementato ogni giorno»**. Dal momento in cui il negozio è aperto, ogni giorno qualcosa migliora. La scommessa è che un brand in cui il loop di miglioramento non si ferma, alla lunga, diventa forte.

E quel loop di miglioramento, per il 99%, lo gira Claude Code.

## Non organizzo, ma è organizzato

Arrivato a questo punto, lo realizzo di nuovo. Quasi nessuna pratica tradizionale di sviluppo — «organizzare», «progettare», «pianificare» — la sto facendo.

Non scrivo CLAUDE.md. Le sessioni vanno a sensazione. Il workflow non è ritualizzato. Non ho diagrammi tecnici, non uso strumenti di task management. Eppure, dalla costruzione all'operatività, le cose vanno avanti.

A voler essere precisi: **l'organizzazione l'ho delegata a Claude**. Io non la faccio, ma Claude Code sì. Quindi, di fatto, lo stato organizzato è mantenuto.

Questa configurazione assomiglia a quella in cui Masayoshi Son dice «facciamolo» e un'unità esecutiva ultra-competente parte e si occupa di organizzare e implementare tutto. **Io resto dal lato di chi decide «facciamolo», e l'unità esecutiva è un'AI.**

Nell'era dell'AI, un individuo è arrivato a poter riprodurre questo schema: è la sensazione più forte che porto a casa da queste tre settimane.

## Per chiudere

Non penso che sia il modo giusto di farlo. Probabilmente, scrivere un CLAUDE.md ben fatto, dividere le sessioni per obiettivo, ritualizzare il workflow — anche quella è una via che sta in piedi.

Però, nel mio caso, **non organizzare è stato più veloce**. Se ho tempo da spendere a organizzare, preferisco passarlo a girare la palla a Claude Code e giudicare quello che torna indietro.

A presto.

— Yoskee  
[moday.me](https://moday.me)

---

<!-- moday-product-card -->
### Indossa il giorno. — Le T-shirt MODAY

| Set | Pezzi | Prezzo |
|---|---|---|
| **[La settimana intera →](https://moday.me/collections/bundle-full-week)** | Mon–Sun (7) | $159 |
| **[La settimana lavorativa →](https://moday.me/collections/bundle-workweek)** | Mon–Fri (5) | $119 |
| **[Pacchetto Starter →](https://moday.me/collections/bundle-starter)** | Mon · Wed · Fri (3) | $79 |
| **[Il weekend →](https://moday.me/collections/bundle-weekend)** | Sat · Sun (2) | $55 |

*Spedizione gratuita oltre $99 · 8 colori × 6 taglie · 9 lingue*
