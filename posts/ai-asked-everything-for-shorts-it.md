<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# Per fare i video short, ho chiesto all'AI tutto quello che non sapevo

## Ritiro quello che avevo scritto sul «loop di osservazione»

In un post precedente avevo scritto che «il loop di osservazione è partito» — che dal momento dell'apertura il mondo aveva cominciato a rispondermi.

Quattro o cinque giorni dopo, ho capito una cosa: **il campione è troppo piccolo per osservare qualunque cosa.**

Posso fissare GA4, seguire i comportamenti del carrello, leggermi i log del chatbot — ma il volume è così basso che non ne esce nessuna ipotesi su cui valga la pena agire. Per iniziare anche solo a teorizzare, bisogna che entri più gente nel negozio.

Quindi la mossa giusta non è ancora osservare. È **far salire prima il traffico.** Avevo invertito l'ordine.

## Mi metto sul serio le mani in pasta sull'acquisizione

Tutta la fase di build era dedicata a **costruire la macchina**. Distribuzione su nove lingue e dieci piattaforme, chatbot automatizzato, automazione ordine→produzione, loop di miglioramento automatico. Tutto sotto la voce «costruisci il sistema, poi lascialo girare».

Volevo che anche l'acquisizione funzionasse così — entra budget pubblicitario, si accumulano i dati, l'AI propone migliorie, automatizzi il loop, fine.

Ma budget pubblicitario non ce n'è, adesso (ne ho parlato in un altro post). Con il paid fuori dai giochi, **l'unica corsia che resta è il social organico**. Nello specifico i video short — per un prodotto così visivo, il formato dovrebbe calzare.

C'è solo un dettaglio: **non ho la più pallida idea di cosa funzioni sugli short in questo momento.**

Gli short giapponesi non li seguo con costanza. Quelli in inglese? Ancora meno. Faccio consulenza e-commerce di mestiere, e questa è una debolezza che devo solo ammettere. Mi sto muovendo su un terreno che non è il mio forte.

## Step uno: chiedo a Gemini

Stavo seguendo le notizie del Google I/O e mi serviva una scusa per provare Gemini sul serio. Quindi gli ho chiesto: «Cosa va forte adesso sui video short rivolti a professionisti business anglofoni, su TikTok, LinkedIn e Shorts?»

Quello che mi è tornato indietro era un mondo di cui non sapevo nulla:

- **Corporate buzzword satire** — sketch che prendono in giro il vocabolario vuoto del corporate speak: «Synergy», «Circle back», «Let's take this offline».
- **«Day in the Life» autoconsapevole** — robe tipo «Come tenere Teams su "Active" senza alzarsi dal letto», che ridono del senso di rotella-nell'ingranaggio.
- **Personaggi alla Corporate Erin** — attori che interpretano la HR fredda, sorriso professionale e parlata veloce che impacchettano un licenziamento in un tono allegro.
- **LinkedIn Lunatics** — TikToker che leggono ad alta voce e sbeffeggiano i post business in versione poesia che la gente pubblica seriamente su LinkedIn.

Il pattern che ha tirato fuori Gemini mi ha colpito forte. Il filo conduttore della viralità dell'humor business anglofono è **«ammutinamento comico contro la cultura aziendale assurda».**

Per definizione è terreno confinante con MODAY. La visione del mondo di una t-shirt «MONDAY: System Booting…» o di una «FRIDAY: Build Successful ✓» vive dentro quella stessa cultura.

Non sarei mai arrivato a quei quattro filoni lavorando solo con la mia testa.

## Step due: passo tutto a Codex e gli chiedo uno storyboard

Ho dato l'output di Gemini direttamente in pasto a Codex. Prompt: «Scrivimi lo storyboard di un video short di acquisizione per MODAY. Verticale 9:16, 22 secondi, pubblico business anglofono, tono satirico-umoristico, chiusura sul brand.»

Quello che è uscito:

![Storyboard: Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

**«Weekdays Ranked by Developer Damage».** Concept: classifica i giorni della settimana in base a quanti danni infliggono a uno sviluppatore. Non una vetrina di prodotto — un **meme che sta in piedi da solo**. Progettato perché i commenti partano a litigare sul ranking, chiuso con «Tell me I'm wrong» come esca. Solo alla fine atterra il brand: «MODAY — Wear the day you survived.»

Il pitch di prodotto è **nascosto negli ultimi due secondi**. Il video non si legge come una pubblicità. Viene consumato come un meme. Sono i commenti a fare il lavoro pesante. La strategia di acquisizione è esattamente la roba che faccio nel mio mestiere di consulente — e questa volta l'ho subappaltata interamente a un'AI.

E il risultato è sensibilmente meglio di quello che avrei scritto io.

## Step tre: tiro su quattro modelli riutilizzabili con ChatGPT Image

Una serie di video ha bisogno di **personaggi che puoi riusare**. Non posso permettermi di scritturare persone vere e non ho il tempo per girare. ChatGPT Image 2.0 mi ha generato quattro modelli in un solo batch.

![Model 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Model 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Model 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Model 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

Etnia, età e genere distribuiti sui quattro. Ognuno mantiene una vibe coerente — da ingegnere, da remote worker, da impiegato in ufficio — ma ogni modello ha la sua faccia.

Ognuno è arrivato con angoli frontale, tre-quarti e di profilo più diverse espressioni, tutto da un singolo prompt. Sono questi il cast ricorrente della serie video. **Quattro modelli interni, esclusivi del brand.**

Affittare uno studio. Chiamare un'agenzia. Procurarsi il guardaroba. Montare la luce. Tutto saltato. Costo praticamente zero. Tempo totale, una mezz'oretta.

## Da qui in poi, lavoro a mano

I passi che restano:

1. Comporre ogni scena come fermo immagine (modello + t-shirt + sfondo).
2. Animare il fermo immagine in video.
3. Aggiungere SFX e didascalie.
4. Pubblicare su TikTok / Instagram Reels / YouTube Shorts.

Per questo giro **lo spread multilingua e l'automazione li sposto allo step successivo.** Prima un solo video in inglese, fatto a mano, buttato nel mondo. Se gira, scalo il pattern vincente su tutte e nove le lingue e costruisco la pipeline di automazione dietro. Se non gira, provo da un'altra angolazione.

È preso dritto dal playbook dello sviluppo web: **costruisci un prototipo funzionante a mano, investi in automazione solo dopo che vedi la forma del vincitore.** L'acquisizione segue la stessa regola.

## AI-driven, ma torno comunque alle mie mani

In un post precedente avevo scritto: «delego all'AI tutto quello che riesco». Quella linea non è cambiata. In questo giro lo storyboard, i modelli e la strategia li ha messi insieme l'AI.

Ma **la composizione e il montaggio del primo video li faccio io, a mano.** Non perché l'AI tecnicamente non potrebbe farlo. Perché **la texture del primo voglio sentirmela sulle mani mie.**

Cosa aggancia. Dove la gente molla. Cosa succede nei commenti. Il criterio di giudizio per la fase di automazione non posso costruirlo se non lo guardo accadere in prima persona. Costruisci a mano, prendi, manca, registra l'esperienza — è **la materia prima per i criteri** che mi serviranno dopo.

Il brand è AI-driven, ma **il giudizio resta mio.** Quando delegare, quando no — quel confine è il lavoro del founder. E adesso è uno dei momenti «fallo a mano».

Per i curiosi, il primo video è questo:

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

Se il primo atterra o tracolla, ancora non lo so. Hit → automazione. Miss → altra angolazione. In entrambi i casi, da qui parte un loop nuovo.

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
