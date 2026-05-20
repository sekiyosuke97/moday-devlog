<!-- canonical: https://moday.me/blogs/engineering/blog-distribution-pipeline -->

# Ein Post, neun Sprachen, zehn Plattformen — die MODAY-Distribution-Pipeline

## Einmal auf Japanisch schreiben, in neun Sprachen an zehn Stellen landen

Das passiert, sobald ich einen japanischen Entwurf für den MODAY-Devlog fertig habe:

| Tier | Ziel |
|---|---|
| Eigene Kanäle | Shopify Blog (JA + 8 Locales) |
| Auto-Distribution per API | dev.to / Qiita / Zenn / GitHub-Devlog |
| Manuelles Einfügen mit vorbereiteten Dateien | note / Medium / Tumblr |

Meine Arbeit auf der Schreibseite: Entwurf fertigmachen, einmal `distribute.py` laufen lassen. Den Rest macht das Ding allein.

Diese Pipeline habe ich in drei Tagen gebaut und jagde seit Post #1 jedes Stück da durch. Hier die tatsächliche Form davon.

## Die Designentscheidung — „Auto" und „Manuell" von Anfang an trennen

Das Erste, was ich festgelegt habe: **die Ziele in zwei Schichten trennen**.

Auf der einen Seite Plattformen mit funktionierender Write-API (Shopify, dev.to, Qiita, Zenn-über-GitHub, GitHub selbst). Auf der anderen Seite Plattformen ohne API oder mit feindseliger API (note, Medium, Tumblr). Sobald du versuchst, beides unter einen Hut zu bekommen, wird das Skript zum Sumpf.

Also:

- Auto-Tier — `distribute.py` macht alles über HTTP
- Manual-Tier — `prepare_handoff.py` spuckt **paste-fertige Dateien** aus, die ein Mensch in die UI trägt

Das Manual-Tier ist der Teil, den ich noch nicht an KI abgeben konnte. Aber alles bis zum Moment des Einfügens ist automatisiert.

## Was `distribute.py` tatsächlich tut

Der Ablauf innerhalb von `distribute.py`:

1. **Hero-Gate beim Start.** Wenn `content/posts/<slug>/hero.png` fehlt, bricht das Skript ab. Kein Coverbild, keine Distribution. Ein struktureller Schutz gegen das „Mist, Hero vergessen."
2. **Post in den Shopify-Journal-Blog**, Body + Hero in einem Schritt.
3. **Shopify-Übersetzungen registrieren.** Liest die Nachbar-Dateien `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` und schiebt alle acht Locales per `translationsRegister`-API in einem Rutsch rein.
4. **POST an dev.to**, EN-Body, Cover ist die Shopify-CDN-URL recycelt.
5. **POST an Qiita**, JA-Body mit `canonical_url` zurück auf Shopify.
6. **Zenn — kein API-Call.** Zenn bietet bewusst keine Write-API, also habe ich die Zenn-↔-GitHub-Sync konfiguriert. Ein Push landet automatisch als Post.
7. **GitHub-Devlog**: committet `<slug>-ja.md`, `<slug>-en.md`, `<slug>-hero.png` ins `moday-devlog`-Repo.
8. **Ruft `prepare_handoff.py` auf**, um die Paste-Dateien fürs Manual-Tier zu erzeugen.
9. **Schreibt `status.json`** neben die Quelle, mit URL/ID/Zeitstempel für jede Plattform.

Die zwei Teile, auf die ich am meisten stolz bin, sind das **Hero-Gate** und die **Zenn-via-GitHub-Route**. Das Hero-Gate macht es strukturell unmöglich, einen Post ohne Coverbild rauszujagen. Und Zenn — das mit Absicht keine Write-API anbietet — kriegt den Post trotzdem, weil ein `git push` als Brücke reicht.

## Was `prepare_handoff.py` tut

Erzeugt paste-fertige Dateien für die drei manuellen Ziele:

| Datei | Inhalt | Sprache |
|---|---|---|
| `note.md` | JA-Original mit Kommentar-Anleitungen zum Einfügen. Tabellen werden in „**Label:** Wert"-Absätze umgewandelt, weil note keine Markdown-Tabellen rendert. | JA |
| `medium.html` | EN-Übersetzung als HTML. Anleitungs-Banner oben mit copy-disabled CSS, Body darunter. ⌘+A → ⌘+C kopiert nur den Body. | EN |
| `tumblr.md` | EN-Lede (H1 bis zur ersten H2, hart gedeckelt bei 1500 Zeichen) + Canonical-Link + Tumblr-typischer Tag-Block. | EN |

Der nicht-offensichtliche Teil hier ist der **Plattform-Dialekt**.

note rendert keine Markdown-Tabellen — wenn du das Rohzeug reinpastest, kriegst du `| header | value |` als Klartext, sieht entsprechend grottig aus. Also schreibt `prepare_handoff.py` jede Tabelle in Bold-Label-Absätze um.

Medium hat das umgekehrte Problem: Copy-Paste von irgendwo zieht meistens Metadaten mit. Ich wollte, dass der Autor (ich) auf der Seite ⌘+A → ⌘+C machen und *nur den Body* in der Zwischenablage haben kann. Also hat das Output-HTML oben einen Anleitungs-Banner mit `user-select: none` CSS — sichtbar für den Autor, unsichtbar für die Zwischenablage.

Die Tumblr-Kultur belohnt es nicht, einen 3.000-Wörter-Essay in einen Post zu kippen. Also nehme ich nur die Lede raus und verlinke zurück aufs Canonical.

Jede Plattform kriegt ihren **Dialekt und ihre Kultur** respektiert — an einer zentralen Stelle.

## Übersetzung lasse ich die KI auch machen — aber nur innerhalb der Subscription

Der ganze MODAY-Pitch ist „ein KI-getriebener Markenbau", also läuft die Übersetzung natürlich auch über KI. Wie genau, habe ich kürzlich geändert.

- Vorher: `distribute.py` rief die Anthropic-API mit Claude Haiku pro Locale auf.
- Jetzt: Ich bitte Claude Code (Opus 4.7) direkt, „rewrite das für acht Locales", in der Session.

Der Grund ist banal und unsexy: **Ich will keine zweite verbrauchsbasierte Rechnung**. Ich zahle bereits für Claude Max. Was innerhalb der Subscription stattfinden kann, soll innerhalb der Subscription stattfinden.

Das ist weniger eine technische als eine **wirtschaftliche Entscheidung**. Für einen Ein-Personen-Laden ist das Wichtigste, die Fixkosten klein zu halten. Eine Claude-Max-Subscription *und* eine verbrauchsbasierte Anthropic-API-Rechnung für denselben Job laufen zu lassen, ist eine schlampige Art, eine persönliche GuV zu führen.

Das andere, was zählt: **Qualität**. Die Haiku-via-API-Outputs lasen sich wie Übersetzungen — brauchbar, aber nicht muttersprachlich. Für neun Locales brauche ich Rewrites, die sich lesen, als hätte sie eine lokale Founder:in vor Ort geschrieben. Ohne das kommt die Marke in keinem dieser Märkte an.

Diese Art Rewrite ist keine Übersetzung; das ist Lokalisierungs-Rewrite. Das über Claude Code auf Opus 4.7 laufen zu lassen, hat mir spürbar besseren Output gegeben als die alte Haiku-API-Pipeline.

Die Kosten gesenkt, die Qualität ist nebenbei gestiegen. Hatte ich nicht kommen sehen.

## Der tatsächliche Tagesablauf

Der operative Rhythmus sieht jetzt so aus:

1. JA-Post in der mobilen Claude-App entwerfen (meistens im Zug).
2. In einer Claude-Code-Session unter `webhook/posts/004-<slug>-ja.md` ablegen.
3. Claude Code bitten, „rewrite für acht Locales" — produziert `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`.
4. Hero mit `webhook/generate_hero.py` generieren → `content/posts/<slug>/hero.png`.
5. `python webhook/distribute.py webhook/posts/004-<slug>-ja.md` ausführen.
   - Auto-Distribution an Shopify (JA + 8 Locales), dev.to, Qiita, GitHub.
   - Ruft `prepare_handoff.py` auf, das `content/posts/<slug>/{note.md, medium.html, tumblr.md}` ablegt.
6. note / Medium / Tumblr im Browser öffnen, die vorbereiteten Dateien einfügen.

Der einzige Schritt, in dem ich tatsächlich *denke*, ist Schritt 1. Der Rest sind Anweisungen an Claude Code, ein Skriptlauf und Einfügen.

## Von „Idee im Zug" bis „alles ist live" an einem Tag

Was mir an dem Ganzen am meisten gefällt, ist nicht mal das Skript — es ist der **menschliche Teil des Ablaufs**.

Ideen kommen mir, wenn ich nicht am Schreibtisch sitze. Beim Pendeln. Direkt vorm Einschlafen. Beim Spazieren. In dem Moment öffne ich die mobile Claude-App, ziehe das MODAY-Projekt auf und rede den Post durch. Bis ich zu Hause bin, ist der Entwurf im Wesentlichen fertig.

Am Schreibtisch öffne ich Claude Code, gebe ihm den Entwurf, es produziert die Locale-Rewrites und fährt die Pipeline.

Die Zeit, die ich *am Schreibtisch sitze und Wörter herumschiebe*, geht gegen Null. Das ist der Teil von „KI-getriebener Markenbau", der sich gerade tatsächlich nach echt anfühlt.

## Zum Schluss

Die Pipeline selbst hat auch Claude Code geschrieben. Ich habe nur gesagt „ich will ein Skript, das in neun Sprachen und an zehn Plattformen verteilt", und die Details haben wir im Gespräch geklärt.

Auf der To-do-Liste bleiben: Tumblr-API-Anbindung, eine Dashboard-Sicht auf `status.json`, automatisches Fan-out in Social. Das baue ich nebenher rein, während die Marke weiterläuft.

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
