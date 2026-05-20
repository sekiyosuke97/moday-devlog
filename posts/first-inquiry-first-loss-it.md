<!-- canonical: https://moday.me/blogs/journal/first-inquiry-first-loss -->

# 24 ore dopo l'apertura: le prime richieste, e la prima vendita che ho già perso

## Aperto il 18/5. Due email il 19/5.

Il 18 maggio ho aperto il negozio, come da piano.

Il post precedente si chiudeva con «apro con la paura ancora attaccata». Il giorno dopo l'apertura, sono arrivate due email.

La prima:

> Hi! Quick question — do you ship to Chicago, Dallas, San Jose
> or is your delivery limited to certain areas?
> Also, how long does it usually take for orders to arrive there?

La seconda:

> Can you deliver to Bavaria, Germany?

Lo dico senza filtri: ero *al settimo cielo*.

Chicago, Dallas, San Jose, la Baviera. Qualcuno di cui non saprò mai nome né faccia era arrivato fino al negozio che avevo costruito ed era abbastanza interessato da **decidere di scrivere un'email**. Quel tipo di prova mi è atterrato davanti per la prima volta.

## Apro GA4. Gli Stati Uniti stavano superando il Giappone.

In parallelo ho aperto GA4. Il primo snapshot delle 24 ore dall'apertura.

![Utenti GA4 per paese](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/first-inquiry-first-loss-ga4-countries.png)

- United States: 22 utenti (44%)
- Japan: 14 utenti (28%)
- Germany: 6 utenti (12%)
- Singapore: 3 utenti
- Canada: 2 utenti
- South Korea: 1 utente

Il paese in cui vivo, quello da cui smanetto sul negozio ogni giorno, finisce **dietro agli Stati Uniti**. La Germania è terza.

È stato il momento in cui il geo-routing e il setup a nove locali si sono ripagati — per la prima volta, in numeri. Nel post precedente avevo scritto «non vedo il cliente». La faccia non è ancora a fuoco. Ma **la geografia grezza di dove si trova** ha cominciato a emergere.

Per la cronaca: gli ordini sono ancora a zero. L'interesse c'è, ma non sta convertendo. Manca qualcosa — ansia sulla spedizione, sui tempi, sul prezzo, sull'estetica. Non so ancora quale di questi, e non lo saprò finché non riesco a osservarlo. È qui che sono adesso.

## Non sono riuscito a rispondere in giornata.

Torno alle email.

Sono arrivate in due. Sono grato. Però **non sono riuscito a rispondere lo stesso giorno**.

Me ne sono accorto a notte fonda, e quella sera avevo lavoro del giorno di mezzo aperto. Ho buttato giù la bozza in giapponese, ho passato le traduzioni a Claude Code per inglese e tedesco, e i messaggi sono usciti per davvero **il giorno dopo**.

La parte di scrittura + traduzione, una volta che il flusso è rodato, sono 5–10 minuti. Ma la latenza tra «è arrivata l'email» e «sono davanti allo schermo» già aggiunge ritardo. In più, rispondere a una domanda sulla disponibilità della spedizione significa controllare i paesi coperti da Gelato, stimare i tempi — mettere insieme una risposta vera richiede una bella fetta di concentrazione.

Sull'email come canale, rispondere entro 24 ore non è considerato scortese. Ma la temperatura dall'altra parte cala parecchio in 24 ore.

La differenza tra un negozio dove «mandi una domanda e la risposta torna in fretta» e uno dove «la risposta arriva il giorno dopo» probabilmente cambia la decisione di acquisto. Soprattutto quando è un brand visto per la prima volta, spedisce a livello internazionale, e il cliente ha pagato il costo di scrivere in inglese.

È stato un chiaro **costo opportunità**. Il primo.

## Quindi lo stesso giorno ho spedito un chatbot.

Dopo aver mandato le risposte in ritardo, mi sono mosso veloce.

**Le stesse domande torneranno.** Disponibilità della spedizione, tempi di consegna, metodi di pagamento, taglie. Risponderci una per una via email è troppo lento come supporto.

Quello stesso giorno ho piazzato un widget di chat in basso a destra nel negozio.

È **costruito direttamente sull'API di Claude**, con supporto a nove lingue. Incorporato nel tema Shopify, risponde nella locale del visitatore in automatico. Le risposte di prima linea su spedizione, tempi, taglie e pagamenti vivono adesso lì dentro.

Tempo di build: **circa 15 minuti**. Ho detto a Claude Code «metti un widget di chat in basso a destra, fai passare i messaggi attraverso l'API di Claude, abbina la lingua alla locale Shopify del visitatore» — e ha funzionato.

Lo stato del negozio a fine giornata: **«se la stessa domanda arriva di nuovo, il cliente non aspetta 24 ore».** Era la mossa disponibile quel giorno.

## Il loop di osservazione è partito.

Fino a questo punto, tutta la fase di build girava su «ipotesi che mi ero costruito dentro la testa».

La t-shirt del-giorno-della-settimana dovrebbe atterrare bene su ingegneri e geek. L'internazionale dovrebbe avere senso. Il modello a nove locali, multi-valuta, magazzino-zero dovrebbe funzionare. Tutto era «dovrebbe».

Questo è cambiato nel momento esatto in cui ho aperto.

GA4 inizia a restituire la spaccatura per paese. Qualcuno manda una domanda specifica via email. I log della chat iniziano a raccogliere ciò di cui i visitatori sono davvero preoccupati.

**Il mondo ha iniziato a rispondere.**

Un «modo per vendere» non ce l'ho ancora. Il primo costo opportunità è già successo. Ma siccome il loop di osservazione è partito, **la prossima mossa non è più una tirata a indovinare**.

L'inizio vero di un brand forse non è quando l'ingegneria è finita, né quando il negozio apre — forse è quando **il loop di osservazione comincia a girare**, e quella è la parte che è iniziata oggi.

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
