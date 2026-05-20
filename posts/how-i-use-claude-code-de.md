<!-- canonical: https://moday.me/blogs/journal/how-i-use-claude-code -->

# Wie ich Claude Code benutze — nicht aufräumen, abgeben, aus dem Bauch heraus

## Ein Rückblick, wie ich mit Claude Code eigentlich arbeite

Bis hierhin habe ich viel über den Bau von MODAY geschrieben, aber **wie ich Claude Code konkret steuere**, kam dabei nie vor.

Stack-Auswahl, Distributions-Pipeline, Lokalisierung in neun Sprachen, der in 15 Minuten zusammengeklopfte Chatbot — das war alles die Seite „**was** ich gebaut habe".

Jetzt ist der Shop draußen, der Betrieb läuft an, und es ist ein guter Moment, einmal auf die Metaebene zu wechseln. Vorab das Fazit: **nicht aufräumen, abgeben, aus dem Bauch heraus**.

Das geht vermutlich ziemlich genau in die entgegengesetzte Richtung dessen, was man sonst so an Claude-Code-Tutorials liest.

## CLAUDE.md hat Claude geschrieben

Der übliche Rat lautet: „**Trag in der CLAUDE.md sauber alle Projektinformationen zusammen.**" Markenkontext, Tech-Stack, Coding-Conventions, Prioritäten. Damit Claude Code den Projektkontext schnell greifen kann — alles vom Menschen vorsortiert. Das ist die Standard-Spielart.

Die CLAUDE.md von MODAY enthält **keine einzige Zeile, die ich selbst geschrieben habe**. Ich weiß nicht mal genau, was drinsteht.

Ganz am Anfang habe ich zu Claude Code gesagt: „Du darfst dir die Datei selber zurechtlegen." Daraufhin hat es angefangen, Markenkontext, Tech-Stack, SKU-Tabelle, Markets-Setup und Phasen-Prioritäten von sich aus zusammenzuziehen. Wenn ich gelegentlich reinschaue, sieht das Ganze vermutlich sauberer aus, als ich es per Hand jemals hingekriegt hätte — und vor allem in einer Form, die Claude selbst gut lesen kann.

Von Anfang bis Ende habe ich das „Aufräumen" nicht ein einziges Mal selbst gemacht. **Die Aufräum-Aufgabe selbst ist auf die Claude-Seite gewandert.**

## Sessions teile ich „aus dem Bauch" auf

Ich arbeite schon in getrennten Sessions. Aber **eine Regel dafür gibt es nicht**.

Ich trenne nicht streng nach Zweck. Es läuft eher grob nach Stimmung: „Content", „UI/UX-Polishing", „MD (Kleinkram)". Bildgenerierung, Übersetzung, Code-Schreiben — das mischt sich alles innerhalb derselben Session.

Ich mache keine „Übersetzungs-Session" und keine „Coding-Session". **Ich schneide nach dem Arbeitsfluss.** Klingt schlampig, hat aber den Effekt, dass „Einfälle aneinander andocken".

Ich schraube am UI rum und merke plötzlich: „Ach, dann sollte ich auch die Übersetzung anpassen." In derselben Session lasse ich die Übersetzung dann gleich mit drüberlaufen. Weil die Kosten, Kontext über Session-Grenzen zu schleppen, bei null liegen, **reißt der Entscheidungsfluss nicht ab**. Das wirkt überraschend stark.

## Technische Anweisungen gebe ich praktisch keine

Habe ich in einem anderen Post schon mal beschrieben: bei der Stack-Auswahl habe ich keine einzige technische Bedingung mitgegeben. Was ich reingereicht habe, waren ausschließlich Business-Anforderungen. Und auch in der Bauphase hat sich an dieser Haltung nichts geändert.

Das einzige, was ich bewusst gesagt habe, ist:

„**Bei Shopify und Gelato bitte den Standard-Pfad gehen, Custom-Implementierungen auf das absolute Minimum.**"

Das ist für mich die eiserne Regel bei SaaS. Innerhalb dessen, wofür der Anbieter sein Produkt vorgesehen hat, zu bleiben, ist langfristig schlicht am stabilsten. Custom-Lösungen sind kurzfristig sexy, brechen aber bei der nächsten Vendor-Aktualisierung. Standard-Flows, Standard-API, Standard-Theme-Struktur. Davon abweichen nur dann, wenn es wirklich nicht anders geht.

Wenn das einmal gesetzt ist, kann ich API-Calls, Test-Strategie, Error Handling und sämtliche Implementierungsdetails komplett an Claude Code abgeben.

## „Sag mir mal" beantworte ich mit „Mach das selbst"

Claude Code fragt einen ab und zu zurück. „Zeig mir bitte den Inhalt der Datei", „Ist das so okay?", „Wie schreibe ich die Tests?"

Auf praktisch alles davon antworte ich: **„Mach das selbst."**

Wenn du dir die Datei anschauen willst, benutz deinen View-Tool. Wenn du eine Entscheidung von mir willst, entscheide selbst. Und tatsächlich liest Claude dann in den allermeisten Fällen selbst nach, trifft die Entscheidung selbst und implementiert direkt weiter.

Das ist die Praxis von dem, was ich in einem anderen Post beschrieben habe: **die Initiative gehört auf die AI-Seite**. Keine Entscheidung zurückspielen, die Entscheidung dort lassen.

Was am Ende übrigbleibt, sind nur noch die **Bereiche, die sich partout nicht per API erledigen lassen**: Bankkonto, Payment-Prüfung, Anmeldungen bei Diensten, Abo-Registrierung, API-Keys ausstellen. Das sind die Stellen, an denen Verträge mit Menschen gemacht werden — da setze ich mich selbst hin. Alles andere liegt auf der Claude-Seite.

## GA4 jeden Tag abklappern lassen und Verbesserungen vorschlagen lassen

Das hier ist eine neue Routine, die erst nach dem Launch dazugekommen ist.

Jeden Tag lasse ich Claude Code GA4 abklappern und **Probleme plus Verbesserungsvorschläge ausspucken**. Ich überfliege das und werfe nur das raus, was offensichtlich daneben ist. Die verbleibenden 60–70 % lasse ich direkt vor Ort implementieren.

Zwischen Vorschlag und Implementierung mache ich nichts außer GO/NO-GO. Code schreiben, Architektur überlegen — quasi null.

Das will ich zum Betriebs-Prinzip erheben: **„Jeden Tag wird mindestens eine Verbesserung tatsächlich live geschaltet."** Vom Moment des Launch an soll jeden Tag irgendetwas am Shop besser geworden sein. Die Wette ist: Eine Marke, deren Verbesserungs-Loop nicht abreißt, wird am Ende stärker.

Und 99 % dieses Loops dreht Claude Code.

## Ich räume nichts auf — und trotzdem ist alles aufgeräumt

Wenn ich das bis hierhin so durchlese, fällt mir etwas auf: Ich mache so gut wie keine der klassischen Engineering-Disziplinen wie „Aufräumen", „Design", „Planung".

Keine handgepflegte CLAUDE.md. Sessions aus dem Bauch. Workflows nicht routiniert. Kein Architektur-Diagramm. Kein Task-Manager. Und trotzdem läuft es vom Build bis in den Betrieb irgendwie rund.

Präziser gesagt: **Das Aufräumen ist an die Claude-Seite delegiert.** Ich räume nicht auf, Claude Code räumt auf. Im Ergebnis bleibt der aufgeräumte Zustand stabil.

Diese Konstellation hat etwas von Masayoshi Son, der einfach „Machen wir" sagt — und dann setzt sich ein hochkarätiges Execution-Team in Bewegung, das Sortierung und Umsetzung komplett übernimmt. **Ich bleibe auf der „Machen-wir"-Seite, und das Execution-Team ist eine AI.**

Dass eine Einzelperson in der AI-Ära diese Konstellation nachstellen kann — das ist das deutlichste Aha-Erlebnis aus diesen drei Wochen.

## Zum Schluss

Ich glaube nicht, dass das die richtige Methode ist. Vermutlich funktioniert auch der Weg, bei dem man die CLAUDE.md ordentlich pflegt, Sessions nach Zweck trennt und Workflows zur Routine schleift — sauber durch.

Bei mir war es nur so, dass **nicht-aufräumen schneller war**. Wenn ich Zeit ins Aufräumen stecken könnte, würde ich diese Zeit lieber damit verbringen, etwas an Claude Code zu werfen und das Ergebnis zu bewerten.

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
