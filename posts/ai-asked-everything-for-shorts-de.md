<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# Um Short-Videos zu machen, habe ich der KI jede einzelne Sache gefragt, die ich nicht wusste

## Ich nehme das mit der „Beobachtungsschleife" wieder zurück

In einem früheren Post habe ich geschrieben, dass „die Beobachtungsschleife angefangen hat sich zu drehen" — dass in der Sekunde, in der ich aufgemacht habe, die Welt anfing zu antworten.

Vier, fünf Tage später ist das, was ich tatsächlich gelernt habe, ein anderes: **die Stichprobe ist viel zu klein, um irgendetwas zu beobachten.**

Ich kann auf GA4 starren, das Warenkorb-Verhalten verfolgen, die Chatbot-Logs durchgehen — aber das Volumen ist so dünn, dass keine Hypothese rauskommt, mit der man wirklich arbeiten kann. Bevor ich überhaupt anfangen kann zu theoretisieren, müssen mehr Leute reinkommen.

Der nächste Spielzug ist also nicht Beobachten. Der nächste Spielzug ist, **zuerst die Reichweite hochzubekommen.** Ich hatte die Reihenfolge falsch.

## Jetzt muss ich mich beim Thema Traffic mal selbst die Hände schmutzig machen

Die gesamte Build-Phase ging darum, **die Maschine zu bauen**. Distribution in neun Sprachen über zehn Kanäle, automatisierter Chatbot, automatisiertes Order→Production, eine automatisierte Improvement-Loop. Alles unter dem Motto „bau das System, dann lass es laufen".

Akquise wollte ich genauso aufziehen — Werbebudget rein, Daten sammeln sich, KI schlägt Verbesserungen vor, Loop automatisieren, fertig.

Nur: gerade gibt es kein Werbebudget (habe ich in einem anderen Post abgehandelt). Wenn Paid wegfällt, **bleibt nur Organic Social als Spur**. Genauer: Short-Video. Bei einem Produkt, das so visuell ist, muss das Format eigentlich passen.

Bis auf ein Detail: **ich habe absolut keine Ahnung, was bei Short-Video gerade funktioniert.**

Ich schaue weder deutsche noch japanische Shorts in irgendeiner ernsthaften Regelmäßigkeit. Englischsprachige Shorts? Noch weniger. Ich mache hauptberuflich E-Commerce-Beratung, und das hier ist eine Schwäche, die ich einfach offenlegen muss. Ich bewege mich in Gelände, das nicht meine Stärke ist.

## Schritt eins: Gemini fragen

Ich hatte sowieso gerade die Google-I/O-News verfolgt und wollte einen Anlass haben, Gemini ernsthaft auszuprobieren. Also habe ich gefragt: „Was trendet aktuell im Short-Video-Bereich für englischsprachige Business-Profis auf TikTok, LinkedIn und Shorts?"

Was zurückkam, war eine Welt, von der ich nichts wusste:

- **Corporate Buzzword Satire** — Sketches, die das hohle Vokabular der Corporate-Sprache aufs Korn nehmen: „Synergy", „Circle back", „Let's take this offline".
- **Selbstironische „Day in the Life"** — Sachen wie „Wie du Teams auf 'Aktiv' hältst, ohne aus dem Bett zu kommen", die das Gefühl, ein Rädchen im Getriebe zu sein, ins Komische ziehen.
- **Corporate Erin-artige Figuren** — Schauspielerinnen, die die eiskalte HR-Persona spielen, professionelles Lächeln und schnelles Sprechtempo, eine Kündigung in fröhlichen Tonfall verpackt.
- **LinkedIn Lunatics** — TikToker, die diese poetisierten Business-Posts, die Leute auf LinkedIn allen Ernstes publizieren, laut vorlesen und veräppeln.

Das Muster, das Gemini rausgezogen hat, hat gesessen. Der rote Faden bei englischsprachigem Business-Humor-Viral-Content ist **„komödiantische Meuterei gegen absurde Corporate-Kultur".**

Per Definition Nachbargelände von MODAY. Das Weltbild eines „MONDAY: System Booting…"-Shirts und eines „FRIDAY: Build Successful ✓"-Shirts wohnt mitten in dieser Kultur.

Auf diese vier Genres wäre ich aus meinem eigenen Kopf heraus niemals gekommen.

## Schritt zwei: Codex das Ganze geben und um ein Storyboard bitten

Ich habe den Gemini-Output direkt an Codex weitergereicht. Prompt: „Schreib das Storyboard für ein MODAY-Akquise-Short. 9:16 vertikal, 22 Sekunden, englischsprachiges Business-Publikum, Ton: Satire und Humor, Landing am Ende auf der Marke."

Was zurückkam:

![Storyboard: Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

**„Weekdays Ranked by Developer Damage".** Konzept: die Wochentage danach ranken, wie viel Schaden sie an einem Developer anrichten. Keine Produktshow — ein **Meme, das für sich allein steht**. So angelegt, dass die Kommentarspalte anfängt, über das Ranking zu streiten, abgeschlossen mit „Tell me I'm wrong" als Köder. Erst ganz am Ende kommt die Marke ins Bild: „MODAY — Wear the day you survived".

Der Produkt-Pitch ist **in den letzten zwei Sekunden versteckt**. Das Video liest sich nicht wie Werbung. Es wird als Meme konsumiert. Die Kommentare machen die Arbeit. Akquisestrategie ist ganz klar Heimspielfeld meiner Beratertätigkeit — und ausgerechnet diesmal habe ich es komplett an die KI delegiert.

Und das Ergebnis ist spürbar besser, als das, was ich selbst hingeschrieben hätte.

## Schritt drei: vier wiederverwendbare Models mit ChatGPT Image aufsetzen

Eine Video-Serie braucht **Figuren, die man wieder einsetzen kann**. Echte Menschen anheuern kann ich mir nicht leisten, Zeit für ein Shooting habe ich nicht. ChatGPT Image 2.0 hat mir in einem Rutsch vier Models erzeugt.

![Model 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Model 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Model 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Model 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

Ethnie, Alter und Geschlecht über die vier verteilt. Jedes behält eine in sich stimmige Note — engineer-haft, remote-worker-haft, office-professional-haft —, aber jedes Model hat sein eigenes Gesicht.

Frontal, Dreiviertel, Seite plus mehrere Mimiken kamen für jeden der vier aus einem einzigen Prompt. Das ist der wiederkehrende Cast für die Video-Serie. **Vier hauseigene Models, exklusiv für die Marke.**

Studio mieten. Agentur anrufen. Garderobe besorgen. Licht aufbauen. Alles übersprungen. Kosten praktisch null. Gesamtzeit, vielleicht dreißig Minuten.

## Ab hier mache ich von Hand weiter

Was noch ansteht:

1. Jede Szene als Standbild komponieren (Model + das Shirt + Hintergrund).
2. Das Standbild zu Video animieren.
3. SFX und Untertitel drauflegen.
4. Auf TikTok / Instagram Reels / YouTube Shorts posten.

Für diese Runde schiebe ich **Multilingual-Fanout und Automatisierung in den nächsten Schritt**. Erstmal ein englisches Video, von Hand gebaut, rausgeschossen. Wenn es zündet, skaliere ich das gewinnende Muster auf alle neun Sprachen und baue dahinter die Automatisierungs-Pipeline. Wenn nicht, probiere ich einen anderen Winkel.

Das ist direkt aus dem Web-Dev-Playbook: **erst einen lauffähigen Prototypen von Hand bauen, erst in Automatisierung investieren, wenn die gewinnende Form sichtbar wird.** Akquise folgt derselben Regel.

## KI-getrieben, und trotzdem trete ich zurück an die eigenen Hände

In einem früheren Post habe ich geschrieben: „Alles, was geht, an KI abgeben." An der Linie hat sich nichts geändert. Diesmal sind Storyboard, Models und Strategie alle KI-gebaut.

Aber **Compositing und Schnitt des ersten Videos mache ich von Hand.** Nicht, weil die KI das technisch nicht könnte. Sondern weil **ich die Textur des ersten Videos in den eigenen Händen spüren will.**

Was zieht. Wo Zuschauer abspringen. Was die Kommentarspalte macht. Das Urteilsvermögen für die Automatisierungsphase entwickele ich nicht, wenn ich nicht selbst dabei zuschaue, während es passiert. Von Hand bauen, treffen, danebenliegen, die Erfahrung wegschreiben — das ist **das Rohmaterial für die Kriterien**, die ich später brauchen werde.

Die Marke ist KI-getrieben, aber **das Urteil bleibt bei mir.** Wann delegiert wird, wann nicht — diese Grenze zu ziehen ist die Aufgabe des Gründers. Und gerade ist einer der „mach es von Hand"-Momente.

Für die Neugierigen, hier ist das erste Video:

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

Ob das erste landet oder gegen die Wand fährt, weiß ich noch nicht. Trifft → Automatisierung. Daneben → anderer Winkel. So oder so beginnt von hier aus eine neue Schleife.

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
