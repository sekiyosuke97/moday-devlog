<!-- canonical: https://moday.me/blogs/journal/15min-chatbot-render-comeback -->

# Ein Chatbot in 15 Minuten — Render rausgeworfen und doch wieder reingeholt

## Vom verpassten Geschäft am 19.05. bis zum laufenden Bot — in 15 Minuten

In einem anderen Post habe ich es schon erwähnt: am 19.05. kamen die ersten zwei Kundenanfragen rein. Beantworten konnte ich sie an dem Tag nicht mehr, die Antworten gingen erst am nächsten Tag raus. Für mich war das ein klares **verpasstes Geschäft** — und genau deshalb habe ich noch am selben Tag einen Chatbot gebaut.

Dieses übliche Widget unten rechts im Shop. Vom ersten Handgriff bis zum live deployten Bot bei Shopify: rund 15 Minuten. Hier steht, was ich davon überblicke — und was nicht.

## Aufbau

Grob sieht es so aus:

- **Frontend**: Widget unten rechts, eingebaut ins Shopify-Theme (wie genau das implementiert ist, weiß ich selbst nicht)
- **Backend**: Render.com, das die Claude API ansteuert
- **Sprache**: gekoppelt an die Shopify-Locale, neun Sprachen
- **Historie**: läuft in ein Google Spreadsheet
- **Eskalation**: Fragen, die der Bot nicht beantworten soll, werden ins Kontaktformular geleitet

Die Designphilosophie ist simpel: **es einfach halten**, mehr nicht. In der Einzelunternehmer-Phase will ich keine Komplexität mitschleppen, egal worum es geht.

## Render rausgeworfen — und doch wieder reingeholt

In einem anderen Post hatte ich angekündigt: „**FastAPI / Render fliegt raus.**" Das klingt jetzt widersprüchlich, aber rausgeflogen ist Render nur für den **Webhook-Job**. Die Verarbeitung der Shopify-Bestellungen, die nach Gelato weitergegeben wurden, lief vorher auf FastAPI auf Render. Das wurde durch eine andere Konstruktion ersetzt (das ist eine eigene Geschichte — gibt's ein anderes Mal als eigenen Post).

Für den Chatbot ist Render jetzt **in anderer Rolle wieder da**. Die Infra, die mal als Webhook-Server lief, und die Infra, die jetzt die Chatbot-API hostet, sind unterschiedliche Dinge: andere Services, andere Prozesse. Nur eben beides bei Render.

„Render rausgeworfen" und „Render in Betrieb" widersprechen sich nicht. Es geht schlicht darum, **für jeden Zweck zu dem Zeitpunkt das passende Werkzeug neu auszuwählen**. Wenn man sich an alte Entscheidungen kettet und sagt „dieses Tool nehme ich nie wieder", wird das Urteilsvermögen starr.

Die Entscheidungsachse liegt bei mir, gebaut wird von Claude Code. Jedes Mal, wenn etwas neu zusammengesetzt wird, holen wir uns das aktuell beste Setup.

## Die Historie liegt in einem Google Spreadsheet

Jede Interaktion zwischen Bot und Nutzer wird in ein Google Spreadsheet geschrieben. Zeitstempel, Locale, die Frage des Nutzers, die Antwort des Bots, ob eskaliert wurde.

Den Vorschlag hat Claude Code gemacht, ich habe ihn übernommen. Im Nachhinein passte das aus drei Gründen erstaunlich gut:

1. **Ich will keine DB aufsetzen**: Schema-Design, laufende Kosten, dann noch Visualisierung drumherum. In der Einzelunternehmer-Phase ist das schlicht zu schwer
2. **Es kostet nichts**: ein Google-Account reicht, keine zusätzlichen Kosten
3. **Wenn ich später analysieren lasse, können sowohl ich als auch Claude Code das sofort lesen**: ein Blick auf die Spalten, und alles ist klar

Punkt drei ist mir am wichtigsten. Wenn ich Claude Code demnächst frage „**fass mir mal die Tendenzen der letzten Anfragen zusammen**", kann es direkt ins Spreadsheet schauen. Bei einer richtigen DB müsste ich Exportskripte schreiben, CSVs erzeugen — ein Schritt mehr.

Eine dedizierte DB wäre sauberer, klar. Aber in der jetzigen Größenordnung reicht das Spreadsheet locker. In der Einzelunternehmer-Phase ist das für mich **die richtige Art von Faulheit**.

## Wie ich die neun Sprachen löse

Ich greife die aktuelle Shopify-Locale ab und reiche sie an den Bot weiter. Der Bot benutzt einen Prompt im Stil von „**bitte in dieser Sprache antworten**" und ruft die Claude API. Dazwischen liegt kein Übersetzungsschritt. Claude schreibt direkt in der Zielsprache.

In einem anderen Post hatte ich geschrieben „**keine Übersetzung, sondern Lokalisierung / Rewrite**" — das gilt für den Bot genauso. Nicht erst auf Japanisch schreiben und dann ins Englische übersetzen, sondern von Anfang an im Duktus eines englischen Native-Speakers antworten. Auf Deutsch eben als deutscher Native. Weil das innerhalb des Modells passiert, fallen sowohl die Latenz der Übersetzung als auch das Risiko von Übersetzungsfehlern strukturell weg.

Auch hier nichts Besonderes. Ich habe in einer Zeile gesagt: „**Locale von Shopify reinnehmen und in der jeweiligen Sprache antworten**", mehr nicht.

## In den Prompt habe ich geschrieben: „kenn dich auf der Seite aus"

Der Bot kann zu den Inhalten der MODAY-Site und zu den Gelato-Produktdaten antworten. Versandfähigkeit, Lieferzeit, Größen, Zahlungsoptionen, Rückgabepolitik, Preise, Bundle-Zusammenstellungen.

Den Auftrag dazu habe ich Claude Code so gegeben: „**halt dich auf der Seite auf dem Laufenden**".

Ich gebe ehrlich zu: **wie genau es das macht, weiß ich nicht**. Steht das alles im Prompt eingebrannt? Wird die Site live gefetcht? Eine Kombination aus beidem? Das hat Claude Code selbst entschieden und implementiert.

Wie in einem anderen Post beschrieben — Anweisung habe ich gegeben, die Umsetzung habe ich abgegeben. Es läuft, die Antworten passen. Für den Moment reicht mir das. Wenn etwas kaputtgeht, sage ich „repariere das" und gut.

## Was er nicht beantworten kann, geht ins Kontaktformular

Es wäre gefährlich, wenn der Bot einfach alles beantwortet.

Individuelle Größenberatung, Geschenkverpackung, B2B-Anfragen, Reklamationen. Wenn der Bot in diesen Bereichen behauptet, würde es später zu Diskrepanzen kommen.

Wenn der Bot entscheidet „besser nicht antworten", leitet er ins Kontaktformular um. Das Design der Guardrails habe ich auch Claude Code überlassen. Was ich gemacht habe, war eine einzige Zeile: „**Fragen, die nicht beantwortet werden können, ins Kontaktformular leiten**".

Welche Frage beantwortet, welche eskaliert wird — die Grenze hat Claude Code gezogen. Ich nehme mir vor, ab und zu in die Logs zu schauen und nachzujustieren, falls die Sortierung offensichtlich danebenliegt. Bisher kam aber nichts auffälliges.

Dass das Ganze in 15 Minuten lief, lag daran, dass in diesen 15 Minuten wenig zu entscheiden war.

„Widget unten rechts", „auf Claude-API-Basis", „neun Sprachen", „Render reaktiviert", „Historie ins Spreadsheet", „Eskalation ins Kontaktformular". Wenn das einmal steht, baut Claude Code den Rest. Ich gebe GO und prüfe, ob es läuft.

Am zweiten Tag nach Shop-Eröffnung war die Basis für automatisierten Support live. Der erste Punkt im **„jeden Tag eine Verbesserung"** — das war dieser hier.

Bis bald.

— Yoskee  
[moday.me](https://moday.me)

---

<!-- moday-product-card -->
### Trag den Tag. — Hol dir die MODAY-Shirts

| Set | Teile | Preis |
|---|---|---|
| **[Die ganze Woche →](https://moday.me/collections/bundle-full-week)** | Mon–Sun (7) | $159 |
| **[Die Arbeitswoche →](https://moday.me/collections/bundle-workweek)** | Mon–Fri (5) | $119 |
| **[Starter-Pack →](https://moday.me/collections/bundle-starter)** | Mon · Wed · Fri (3) | $79 |
| **[Das Wochenende →](https://moday.me/collections/bundle-weekend)** | Sat · Sun (2) | $55 |

*Gratisversand ab 99 $ · 8 Farben × 6 Größen · 9 Sprachen*
