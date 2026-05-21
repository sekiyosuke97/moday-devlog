<!-- canonical: https://moday.me/blogs/journal/15min-chatbot-render-comeback -->

# Un chatbot in 15 minuti — avevo mollato Render, e ci sono tornato

## Dall'occasione persa del 19/5 al «funziona» di quindici minuti dopo

L'ho già raccontato altrove, ma il 19 maggio sono arrivate le prime due richieste dal modulo contatti. Non sono riuscito a rispondere in giornata; la replica è partita il giorno dopo. L'ho registrata come **occasione persa** e, nella stessa giornata, ho messo su un chatbot.

Quel widget che vedi spuntare in basso a destra di un negozio, esatto. Dal momento in cui ho cominciato a quando è andato live su Shopify e ha iniziato a rispondere: circa quindici minuti. Lascio qui il dietro le quinte, almeno per quello che effettivamente so.

## Architettura

A grandi linee, è così.

- **Front-end**: un widget in basso a destra nel tema Shopify (come sia implementato di preciso, non lo so)
- **Back-end**: su Render.com, chiama l'API di Claude
- **Lingua**: agganciata al locale di Shopify, nove lingue
- **Storico**: scritto su un foglio Google
- **Escalation**: le domande a cui non sa rispondere vengono dirottate sul modulo contatti

La filosofia di design è semplice, e si riassume in: **tieni le cose semplici**. In fase di ditta individuale, qualunque cosa io faccia, non voglio portarmi dietro complessità.

## Avevo mollato Render, e ci sono tornato

In un altro post avevo anticipato che «**FastAPI / Render l'ho ormai smontato**». Sembra una contraddizione, ma quel che ho smontato era l'uso come **server di webhook**. La logica che riceve gli ordini Shopify e li smista a Gelato girava in FastAPI su Render. Quella parte è stata sostituita con un'altra configurazione (è una storia che da sola merita un post, alla prossima).

Il chatbot, invece, ha fatto **resuscitare quello stesso Render in un'altra veste**. L'infrastruttura che faceva da server webhook e l'infrastruttura che fa da API per il chatbot: ruoli diversi, servizi diversi, processi diversi. È solo lo stesso Render, sotto.

«Render l'ho mollato» e «sto usando Render» non sono in contraddizione. È solo **scegliere, per ogni uso, lo strumento ottimale in quel momento**. Se ti incateni alle decisioni passate e dichiari «non lo uso più», il tuo giudizio si irrigidisce.

L'asse decisionale resta in mano mia. L'implementazione la cuce Claude Code. A ogni ricostruzione, prendo l'ottimo locale di quel momento.

## Lo storico lo salvo in un Google Sheet

Tutti gli scambi tra bot e utente vengono scritti su un Google Sheet. Data e ora, locale, domanda dell'utente, risposta del bot, se c'è stata escalation.

È stata una proposta di Claude Code, e l'ho accettata. Rileggendola dopo, è caduta a fagiolo per tre motivi.

1. **Non voglio tirare su un DB**: ci vuole lo schema, ci vuole il costo di gestione, ci vuole un layer di visualizzazione. Per una ditta individuale, è troppo
2. **È gratis**: basta un account Google, costo zero
3. **Quando dopo lo faccio analizzare, sia io sia Claude Code lo leggiamo al volo**: scorri le colonne e vedi tutto

Il punto 3 pesa più degli altri. La prossima volta che chiederò a Claude Code «riassumimi i trend recenti delle richieste», andrà a leggere direttamente lo Sheet. Se fosse un DB, dovrei scrivere uno script di estrazione, sputare un CSV — un passaggio di troppo.

Un DB dedicato sarebbe più pulito, sì, ma per la scala attuale lo Sheet basta e avanza. In fase di ditta individuale, considero questo il **sano essere pigri**.

## Le nove lingue, come le gestisco

Prendo il locale corrente di Shopify e lo passo al bot. Il bot manda all'API di Claude un prompt che dice «**rispondi in questa lingua**». In mezzo non c'è alcuno step di traduzione. È Claude che scrive direttamente in quella lingua.

In un altro post ho scritto che «non è traduzione, è localizzazione-rewrite». Lo stesso vale qui. Non si scrive in giapponese e si traduce in italiano: si risponde fin dall'inizio nello stile di un madrelingua italiano. In tedesco, si risponde come un madrelingua tedesco. Tutto questo si chiude dentro il modello, quindi la latenza di traduzione e il rischio di errori vengono ridotti per costruzione.

Anche qui non ho fatto nulla di speciale. Una riga: «**ricevi il locale di Shopify e rispondi in quella lingua**». Stop.

## Nel prompt ho scritto «conosci le info del sito»

Il bot sa rispondere sulle informazioni presenti sul sito MODAY e sui prodotti Gelato. Disponibilità di spedizione, tempi di consegna, taglie, metodi di pagamento, politica di reso, prezzi, composizione dei bundle.

Ho chiesto a Claude Code di «**conoscerle**».

Lo dico onestamente: **come gliele abbia fatte conoscere, io non lo so**. Se sia tutto dentro al prompt, se faccia fetch del sito, se sia un mix delle due — è stato Claude Code a decidere e implementare.

Come ho scritto in un altro post: l'indicazione l'ho data, l'implementazione l'ho lasciata a lui. Funziona, le risposte sono sensate, e per ora mi basta. Se si rompe, dirò a Claude Code «sistemamelo».

## Quello che non sa rispondere lo dirotto sul modulo contatti

Lasciare che il bot risponda a tutto è pericoloso.

Consigli personalizzati su una taglia specifica, confezione regalo, B2B, gestione di problemi. Su questi terreni, se il bot si lascia andare in dichiarazioni nette, dopo si traduce in discrepanze.

Quando il bot giudica «su questa non è meglio rispondere», dirotta sul modulo contatti. Anche il design del guardrail l'ho passato a Claude Code. Quello che ho fatto io è stata una riga: «**fai in modo che le domande a cui non puoi rispondere vengano indirizzate al modulo contatti**».

Quali domande risponde il bot e quali fa salire al supporto: anche quel confine l'ha disegnato Claude Code. Ogni tanto darò un'occhiata ai log; se vedo smistamenti palesemente storti, regolo. Per ora non è successo.

I quindici minuti sono stati possibili perché, dentro quei quindici minuti, le cose da pensare erano poche.

«In basso a destra», «basato su Claude API», «nove lingue», «Render resuscitato», «storico su Sheet», «escalation sul modulo contatti». Definiti questi, il resto lo cuce Claude Code. Io do il GO e controllo che giri.

A due giorni dall'apertura del negozio, l'infrastruttura di automazione del supporto ha iniziato a girare. Il primo dei «**un miglioramento al giorno**» è stato questo.

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
