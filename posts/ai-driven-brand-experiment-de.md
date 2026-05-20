<!-- canonical: https://moday.me/blogs/journal/ai-driven-brand-experiment -->

# Vier Dinge, die selbst KI mir nicht abnehmen kann

Ich baue MODAY — eine Ein-Personen-T-Shirt-Marke mit Wochentags-Prints — und versuche, jeden einzelnen Arbeitsschritt an KI abzugeben. Drei Tage später: vier Dinge haben sich geweigert mitzuziehen.

## Warum ich das eigentlich mache

Die offensichtliche Hälfte des Warums steht woanders: ein japanisches „Es-tut-mir-leid"-T-Shirt, das viral ging, und die Tatsache, dass im Homeoffice die Wochentage ineinander verschwimmen. Das ist die Oberfläche.

Die andere Hälfte traut man sich seltener auszusprechen — ich will herausfinden, wie man im KI-Zeitalter Unternehmen baut, bevor es alle anderen tun.

Mein Hauptjob ist E-Commerce-Beratung. Ich sehe genug Operatives von innen. Als generative KI vor zwei, drei Jahren plötzlich groß wurde, hat sich eine Frage festgesetzt und ist nie wieder gegangen: wie viel von einem Unternehmen kann KI tatsächlich operativ führen?

Lesen beantwortet das nicht. Twitter beantwortet das nicht. Paper beantworten das nicht. Die Frage ergibt sich nicht durch Konsum von Information — sie ergibt sich durch ein echtes Unternehmen, durch das echtes Geld fließt.

Also ist MODAY eine Marke. Aber gleichzeitig ein Ein-Personen-Experiment in der richtigen Größe, um etwas zu messen. Null Lagerbestand. Solo. Global von Tag eins. Drei Tage bis Launch. Echtes Geld, echte Kund:innen, echte Pakete. Bei Hobbyprojekten und internen Pilotphasen wird das Urteilsvermögen weich. Ohne Skin in the Game misst man nichts.

Die Regel: keine Trennlinien. Alles abgeben. Schauen, was nicht mitzieht.

## Drei Tage drin, null Reue

Den „das hätte ich nicht der KI überlassen sollen"-Moment hatte ich noch nicht. Nicht bei der Stack-Wahl. Nicht beim Design. Nicht beim Store, den Webhooks, den Übersetzungen, dem Copy. Ich habe Claudes Output über den gesamten Bau hinweg fast unverändert übernommen.

Klingt nach Eigenwerbung. Ist es nicht. Die ehrliche Lesart ist düsterer — ich habe Claude auch meine Urteilskriterien überlassen. Es gibt in mir gar nichts mehr, woran man Reue festmachen könnte. Hätte ich an meiner eigenen Meinung festgehalten, käme früher oder später ein Moment des „Moment, ich wäre eigentlich anders gegangen". Der Moment ist nicht da.

Im Guten wie im Schlechten.

## Und doch — vier Dinge blieben bei mir

Trotz aller Keine-Trennlinien-Rhetorik haben sich vier Teile dieses Baus geweigert, delegiert zu werden. Durch Subtraktion, in dieser Reihenfolge:

**1. Die Entscheidung, überhaupt einen Prompt zu schicken.**

Der erste Satz, den ich Claude tippe — „was machen wir als nächstes?" — kommt nach wie vor von mir. Jedes Mal. Ich bekomme es nicht weg.

Wenn ich auch das abgeben kann, bin ich auf der nächsten Stufe. Bin ich nicht.

**2. Bankkonto und Zahlungs-KYC.**

Shopify-Payments-Prüfung. Stripe-Identitätsverifikation. Konten für internationale Auszahlungen eröffnen. Hier kommt nichts außer einem Menschen durch. Du erscheinst mit Personalausweis, unterschreibst mit deinem Namen und deinem Gesicht und wirst zur Vertragspartei.

**3. Anmeldungen bei Diensten und Kreditkarte hinterlegen.**

Gelato. Render. fal.ai. Make.com. Anthropic. Bei jedem Konto erstellen, Karte eintragen, auf Bezahltarif klicken. Jede Anmeldung ist meine Hand im Dashboard.

**4. API-Key generieren — bis zum Moment der Übergabe.**

Damit Claude Code eine API aufrufen kann, muss der Key existieren. Den Button „Neuen Key erzeugen" drücke ich. Sobald der Key in der `.env` liegt, hört er auf, meiner zu sein.

Das ist die komplette Liste. In drei Tagen sind das die einzigen Stellen, an denen sich meine Hand physisch bewegt hat. Alles andere fährt Claude.

## Auch Punkt 1 will ich loswerden

Von den vieren ist es Punkt 1, den ich am dringendsten loswerden will — die Entscheidung, überhaupt zu prompten.

Die Version, auf die ich hinarbeite: Claude Code kommt zu mir mit „das ist die nächste Aufgabe", ich antworte nur mit Ja oder Nein, und die Richtung des Unternehmens wandert vollständig auf die KI-Seite.

Technisch geht das vermutlich heute schon. Mit einem Agenten-Setup kann Claude Code Aufgaben selbst aufteilen, sie implementieren und die nächste vorschlagen — in einer Schleife. Es gibt Leute, die genau das gerade fahren.

Im aktuellen Zustand von MODAY bin ich da nicht. Ein Teil von mir will die Richtung des ersten Schritts noch selbst setzen. Ehrlich gesagt ist genau das der Punkt. Den loszulassen ist mein nächster Schritt.

## Die anderen drei sind nicht das Limit der KI — sondern das des Systems

Das ist die Zeile, die ich am liebsten geschrieben habe.

Die Bank, die KYC, die Anmeldungen, die API-Keys — keiner dieser Punkte ist bei mir geblieben, weil „der KI das Urteilsvermögen fehlt". Das ist nicht der Grund.

Der eigentliche Grund ist institutionell. KI hat keine Rechtspersönlichkeit. Weder als natürliche Person noch als juristische. Sie kann nicht Vertragspartei sein. Mehr ist da nicht.

Technisch könnte ich Claude Code mit Browser-Automatisierung wahrscheinlich morgen sagen, das alles zu machen. Formular ausfüllen. Ausweisfoto hochladen. Bestätigungs-E-Mail anklicken. Computer Use existiert. Der Blocker ist nicht die Fähigkeit.

Der Blocker ist, dass auch dann, wenn Claude die Klicks macht, **die eingetragene Partei immer noch ich wäre.** Claude würde nur Formulare unter meinem Namen ausfüllen. Die Haftung bleibt beim Menschen.

Damit sind die drei „nur Mensch"-Punkte nicht die Grenze der KI. Sie sind die Stellen, an denen die gesellschaftlichen Institutionen noch nicht nachgezogen haben. An dem Tag, an dem eine KI selbst rechtlich Betreiberin eines Unternehmens sein kann, wandern auch diese drei.

## Subtraktion, nicht Trennung

Das Framing „was macht der Mensch, was macht die KI" wird in drei Jahren alt aussehen.

In dem Moment, in dem du die Linie ziehst — „Mensch hier, KI dort" — wird die Linie zur Einschränkung. Und die Frage „wie weit kommt KI eigentlich?" wird aus diesem Raster heraus unbeantwortbar. Du kannst die Grenze nicht messen, wenn du sie vorher definiert hast.

MODAY ist deshalb keine Trennung. Es ist der Versuch, alles abzugeben und durch Subtraktion zu prüfen, was nicht mitgegangen ist.

Vier Dinge sind geblieben. Drei sind institutionell. Eines ist mein eigener Antrieb.

Die drei löst die Zeit. Das eine — das muss ich selbst loslassen.

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
