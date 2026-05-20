<!-- canonical: https://moday.me/blogs/journal/first-inquiry-first-loss -->

# 24 Stunden nach Launch: die ersten Anfragen — und der erste Verkauf, den ich schon verloren habe

## Am 18.05. aufgemacht. Am 19.05. lagen zwei Mails im Posteingang.

Ich habe den Shop am 18.05. aufgemacht. Wie geplant.

Der letzte Post endete mit „aufmachen, mit der Angst, die noch dranhängt". Den Tag darauf kamen zwei Mails rein.

Die erste:

> Hi! Quick question — do you ship to Chicago, Dallas, San Jose
> or is your delivery limited to certain areas?
> Also, how long does it usually take for orders to arrive there?

Die zweite:

> Can you deliver to Bavaria, Germany?

Ganz ehrlich: ich war *aus dem Häuschen*.

Chicago, Dallas, San Jose, Bayern. Irgendjemand, dessen Namen und Gesicht ich nie kennen werde, hat zu dem Shop gefunden, den ich gebaut habe — und war neugierig genug, **sich aktiv hinzusetzen und eine Mail zu schreiben**. Diese Art von Evidenz lag zum allerersten Mal vor mir.

## GA4 aufgemacht — die USA lagen vor Japan.

Parallel dazu habe ich in GA4 reingeschaut. Der erste 24-Stunden-Snapshot nach dem Launch.

![GA4 Nutzer nach Land](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/first-inquiry-first-loss-ga4-countries.png)

- United States: 22 users (44%)
- Japan: 14 users (28%)
- Germany: 6 users (12%)
- Singapore: 3 users
- Canada: 2 users
- South Korea: 1 user

Das Land, in dem ich sitze, das Land, von dem aus ich jeden Tag am Shop herumdrücke, liegt **hinter den USA auf Platz zwei**. Deutschland kommt auf Platz drei.

Das war der Moment, in dem das Geo-Routing und das Setup mit neun Locales zum ersten Mal in Zahlen aufgegangen sind. Im letzten Post habe ich geschrieben: „Ich sehe den Kunden nicht." Das Gesicht ist immer noch nicht scharf. Aber die **grobe Geografie, wo diese Leute sitzen**, fängt an, sich abzuzeichnen.

Zur Klarstellung: Bestellungen stehen weiterhin bei null. Interesse ist da, es konvertiert nur noch nicht. Irgendetwas fehlt — Versand-Unsicherheit, Lieferzeit, Preis, der Look. Welches davon, weiß ich noch nicht, und ich werde es erst wissen, wenn ich es beobachten kann. Genau da stehe ich gerade.

## Ich habe es nicht geschafft, am selben Tag zu antworten.

Zurück zu den Mails.

Zwei sind reingekommen. Dafür bin ich dankbar. Aber ich **habe es nicht geschafft, am selben Tag zu antworten**, an dem sie ankamen.

Ich habe sie spät abends gesehen, und ich hatte an dem Abend noch Brotjob-Arbeit am Laufen. Ich habe die Antwort auf Japanisch geschrieben, sie mit Claude Code ins Englische und Deutsche übersetzt — und die Mails sind tatsächlich erst **am Tag darauf** rausgegangen.

Das Drafting plus Übersetzen selbst sind, wenn man eingespielt ist, 5–10 Minuten. Aber die Latenz zwischen „Mail kam rein" und „ich sitze vor dem Bildschirm" zieht es schon auseinander. Dazu kommt: eine Versandfrage seriös beantworten heißt, Gelatos abgedeckte Länder zu checken, Lieferzeiten abzuschätzen — eine richtige Antwort zusammenzubauen kostet einen echten Fokusblock.

Für E-Mail als Kanal gilt: innerhalb von 24 Stunden zu antworten ist nicht unhöflich. Aber die Temperatur auf der Gegenseite fällt in 24 Stunden ziemlich deutlich.

Der Unterschied zwischen einem Shop, bei dem „du schickst eine Frage rein und kriegst schnell eine Antwort zurück", und einem, bei dem „die Antwort kommt am nächsten Tag" — der verändert wahrscheinlich die Kaufentscheidung. Erst recht bei einer Marke, die der Kunde zum ersten Mal sieht, die international verschickt, und bei der er die Mühe in Kauf genommen hat, auf Englisch zu schreiben.

Das war glasklar **Opportunitätskosten**. Die ersten.

## Also habe ich am selben Tag einen Chatbot rausgehauen.

Nachdem die verspäteten Antworten draußen waren, bin ich sofort drangegangen.

**Dieselben Fragen kommen wieder.** Versandverfügbarkeit, Lieferzeit, Bezahlmethoden, Größen. Das einzeln per Mail abzuarbeiten ist als Support viel zu langsam.

Noch am selben Tag habe ich ein Chat-Widget unten rechts in den Shop reingesetzt.

Aufgesetzt **direkt auf der Claude API**, neun Sprachen. In das Shopify-Theme eingebettet, antwortet automatisch in der Locale des Besuchers. Erste-Linie-Antworten zu Versand, Lieferzeit, Größen und Bezahlung liegen jetzt da drin.

Build-Zeit: **ungefähr 15 Minuten**. Ich habe Claude Code gesagt „setz unten rechts ein Chat-Widget hin, route Nachrichten durch die Claude API, Sprache nach Shopify-Locale des Besuchers" — und es lief.

Status des Shops am Ende dieses Tages: **„falls dieselbe Frage gleich nochmal reinkommt, wartet der Kunde keine 24 Stunden mehr."** Das war der Spielzug, der an diesem Tag möglich war.

## Die Beobachtungsschleife läuft.

Bis zu diesem Punkt lief die gesamte Build-Phase auf „Hypothesen, die ich mir in meinem eigenen Kopf zurechtgelegt habe".

Wochentags-Shirts müssten bei Engineers und Geeks landen. International müsste Sinn ergeben. Das Modell mit neun Locales, mehreren Währungen, null Lagerbestand müsste funktionieren. Alles „müsste".

In der Sekunde, in der ich aufgemacht habe, hat sich das geändert.

GA4 liefert plötzlich Country-Breakdowns. Jemand schickt eine konkrete Frage per Mail. Die Chat-Logs fangen an einzusammeln, worüber sich die Besucher tatsächlich Gedanken machen.

**Die Welt hat angefangen zu antworten.**

Eine „Methode zum Verkaufen" habe ich immer noch nicht. Die ersten Opportunitätskosten sind schon angefallen. Aber weil die Beobachtungsschleife jetzt läuft, ist **der nächste Spielzug kein Bauchgefühl mehr**.

Der eigentliche Start einer Marke ist vielleicht weder der Moment, an dem die Engineering-Arbeit fertig ist, noch der Moment, an dem der Shop aufmacht — sondern der Moment, an dem **die Beobachtungsschleife anfängt, sich zu drehen**. Und genau dieser Teil hat heute begonnen.

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
