<!-- canonical: https://moday.me/blogs/engineering/blog-distribution-pipeline -->

# Un post, nove lingue, dieci piattaforme: la pipeline di distribuzione di MODAY

## Scrivo una volta in giapponese, atterra in nove lingue su dieci posti

Ecco cosa succede ogni volta che chiudo una bozza in giapponese per il devlog di MODAY:

| Livello | Destinazione |
|---|---|
| Proprietà mia | Shopify Blog (JA + 8 locali) |
| Distribuito automaticamente via API | dev.to / Qiita / Zenn / GitHub devlog |
| Paste manuale, ma con file di handoff già pronti | note / Medium / Tumblr |

Tutto quello che devo fare lato scrittura è: chiudere la bozza, lanciare `distribute.py` una volta. Il resto si propaga da solo.

Ho montato questa pipeline in tre giorni, e ci faccio passare ogni post dal numero uno. Qui sotto la forma reale della cosa, senza romanticismi.

## La scelta di design: separare «auto» e «manuale» fin dall'inizio

La prima decisione è stata **dividere le destinazioni in due livelli**.

Da una parte le piattaforme con un'API di scrittura che funziona (Shopify, dev.to, Qiita, Zenn-via-GitHub, GitHub stesso). Dall'altra quelle senza API, o con un'API ostile (note, Medium, Tumblr). Nel momento in cui provi a unificarle, lo script diventa una palude.

Quindi:

- Livello auto — `distribute.py` fa tutto via HTTP
- Livello manuale — `prepare_handoff.py` sputa **file pronti da incollare** che un umano porta nella UI

Il livello manuale è la parte che ancora non sono riuscito a passare all'IA. Ma tutto quello che sta prima del momento dell'incollata è automatizzato.

## Cosa fa davvero `distribute.py`

Il flusso interno è questo:

1. **Hero gate all'avvio.** Se `content/posts/<slug>/hero.png` manca, lo script si ferma. Senza immagine di copertina, niente distribuzione. È una protezione strutturale contro il classico «cavolo, mi sono dimenticato l'hero».
2. **Pubblica sul blog Shopify Journal**, corpo del post + hero in un colpo solo.
3. **Registra le traduzioni Shopify**. Legge i file fratelli `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` e infila tutte e otto le locali via `translationsRegister` in un'unica batch.
4. **POST su dev.to**, corpo EN, con l'URL del CDN Shopify riutilizzato come cover.
5. **POST su Qiita**, corpo JA con `canonical_url` che rimanda a Shopify.
6. **Zenn — nessuna chiamata API**. Zenn non espone un'API di scrittura, quindi ho configurato la sincronizzazione Zenn ↔ GitHub. Un push pubblica un post automaticamente.
7. **GitHub devlog**: commit di `<slug>-ja.md`, `<slug>-en.md`, `<slug>-hero.png` nel repo `moday-devlog`.
8. **Chiama `prepare_handoff.py`** per generare i file del livello manuale.
9. **Scrive `status.json`** accanto al sorgente, registrando URL/ID/timestamp di ogni piattaforma.

Le due parti che mi soddisfano di più sono l'**hero gate** e la **rotta Zenn-via-GitHub**. L'hero gate rende strutturalmente impossibile spedire un post senza copertina. E Zenn — che deliberatamente non espone API di scrittura — il post lo riceve lo stesso, perché un `git push` è tutto quello di cui ha bisogno il ponte.

## Cosa fa `prepare_handoff.py`

Produce file pronti da incollare per le tre destinazioni manuali:

| File | Contenuto | Lingua |
|---|---|---|
| `note.md` | Originale JA con commenti di istruzione per il paste. Le tabelle vengono convertite in paragrafi «**Etichetta:** valore» perché note non renderizza le tabelle Markdown. | JA |
| `medium.html` | Traduzione EN in HTML. Banner di istruzioni in alto con CSS che ne disabilita la selezione, corpo sotto. ⌘+A → ⌘+C copia solo il corpo. | EN |
| `tumblr.md` | Lede EN (dall'H1 fino al primo H2, hard-cap a 1500 caratteri) + canonical link + blocco di tag in stile Tumblr. | EN |

Il punto non ovvio qui è il **dialetto per piattaforma**.

note non renderizza le tabelle Markdown — incolli la versione raw e ti compare `| header | value |` come testo letterale, che fa pena. Quindi `prepare_handoff.py` riscrive ogni tabella in paragrafi con etichetta in grassetto.

Medium ha il problema opposto: il copia-incolla da qualsiasi fonte tende a trascinarsi dietro metadati. Volevo che chi scrive (io) potesse fare ⌘+A → ⌘+C sulla pagina e portare via *solo il corpo*. Quindi l'HTML in uscita ha in cima un banner di istruzioni con `user-select: none` — visibile a chi scrive, invisibile alla clipboard.

La cultura di Tumblr non premia chi ci scarica dentro saggi da 3.000 parole. Quindi estraggo solo il lede e rimando al canonical.

Ogni piattaforma riceve il rispetto del suo **dialetto e della sua cultura**, in un unico posto centralizzato.

## La traduzione la passo all'IA — ma solo dentro l'abbonamento

L'intero pitch di MODAY è «un brand costruito guidato dall'IA», quindi ovvio che anche la traduzione vada all'IA. Recentemente ho cambiato il *come*.

- Prima: `distribute.py` chiamava l'API Anthropic con Claude Haiku per ogni locale.
- Adesso: chiedo direttamente a Claude Code (Opus 4.7) di «riscrivere per otto locali», in sessione.

Il motivo è banale e poco glamour: **non voglio una seconda bolletta a consumo**. L'abbonamento Claude Max già lo pago. Tutto quello che può succedere dentro quell'abbonamento, deve succedere dentro quell'abbonamento.

Questa è meno una scelta tecnica e più una scelta **da imprenditore**. Per una bottega di una persona sola, la cosa più importante è tenere giù i costi fissi. Far girare un abbonamento Claude Max *e* contemporaneamente un addebito a consumo sull'API Anthropic per lo stesso task è un modo trasandato di gestire il P&L personale.

L'altra cosa che pesava: la **qualità**. Le uscite di Haiku-via-API si leggevano come traduzioni — utilizzabili, ma non native. Andare in nove locali vuol dire che mi servono riscritture che si leggano come se un founder locale le avesse scritte lui, sul posto. Senza quello, il brand non atterra in nessuno di quei mercati.

Quel tipo di riscrittura non è traduzione; è localizzazione-riscrittura. Farla passare per Claude Code su Opus 4.7 mi ha dato un output sensibilmente migliore rispetto alla vecchia pipeline Haiku-API.

Tagliando il costo, è salita anche la qualità. Non me lo aspettavo.

## La giornata tipo, in pratica

Il ritmo operativo adesso è questo:

1. Scrivo la bozza JA nell'app Claude su mobile (di solito in treno).
2. In una sessione di Claude Code, la deposito in `webhook/posts/004-<slug>-ja.md`.
3. Chiedo a Claude Code di «riscrivere per otto locali» — produce `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`.
4. Genero l'hero con `webhook/generate_hero.py` → `content/posts/<slug>/hero.png`.
5. Lancio `python webhook/distribute.py webhook/posts/004-<slug>-ja.md`.
   - Distribuisce in automatico su Shopify (JA + 8 locali), dev.to, Qiita, GitHub.
   - Chiama `prepare_handoff.py` per piazzare `content/posts/<slug>/{note.md, medium.html, tumblr.md}`.
6. Apro note / Medium / Tumblr nel browser, incollo i file già preparati.

L'unico passo dove uso davvero il *cervello* è il numero 1. Tutto il resto è istruzioni a Claude Code, esecuzione di uno script e incollata.

## Da «mi è venuta un'idea in treno» a «è tutto online» nello stesso giorno

La parte che mi piace di più di tutto questo non è nemmeno lo script — è il **flusso lato umano**.

Le idee mi arrivano quando sono lontano dalla scrivania. In commuting. Subito prima di dormire. Camminando da qualche parte. È in quei momenti che apro Claude su mobile, richiamo il progetto MODAY, e parlo del post. Quando arrivo a casa, la bozza è praticamente fatta.

Alla scrivania, apro Claude Code, gli passo la bozza, lui produce le riscritture per locale e fa girare la pipeline.

Il tempo che passo *seduto a una scrivania a spostare parole avanti e indietro* è vicino a zero. Quella è la parte di «brand costruito guidato dall'IA» che, in questo momento, mi sembra davvero reale.

## Per chiudere

Anche la pipeline in sé l'ha scritta Claude Code. Io ho solo detto «voglio uno script che distribuisca in nove lingue su dieci piattaforme», e abbiamo lavorato le specifiche parlando.

Sulla to-do ci sono ancora cose: integrare l'API Tumblr, una vista a dashboard di `status.json`, fan-out automatico sui social. Le aggiungerò mano a mano che il brand cammina.

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
