<!-- canonical: https://moday.me/blogs/journal/first-inquiry-first-loss -->

# 24 heures après l'ouverture : les premières questions, et la première vente que j'ai déjà perdue

## Ouverture le 18/05. Deux mails le 19/05.

J'ai ouvert la boutique le 18/05, comme prévu.

Le billet précédent se terminait sur « j'ouvre avec la peur encore accrochée ». Le lendemain de l'ouverture, deux mails sont tombés.

Le premier :

> Hi! Quick question — do you ship to Chicago, Dallas, San Jose
> or is your delivery limited to certain areas?
> Also, how long does it usually take for orders to arrive there?

Le deuxième :

> Can you deliver to Bavaria, Germany?

Honnêtement : j'étais *aux anges*.

Chicago, Dallas, San Jose, la Bavière. Quelqu'un dont je ne connaîtrai jamais ni le nom ni le visage avait trouvé son chemin jusqu'à la boutique que j'avais montée, et était assez intéressé pour **prendre la décision d'écrire un mail**. Cette preuve-là est atterrie devant moi pour la première fois.

## J'ai ouvert GA4. Les US dépassaient le Japon.

En parallèle, j'ai regardé GA4. Le premier snapshot des 24 heures depuis l'ouverture.

![Utilisateurs GA4 par pays](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/first-inquiry-first-loss-ga4-countries.png)

- United States: 22 users (44%)
- Japan: 14 users (28%)
- Germany: 6 users (12%)
- Singapore: 3 users
- Canada: 2 users
- South Korea: 1 user

Le pays dans lequel je vis, celui depuis lequel je tripote la boutique chaque jour, arrive **derrière les États-Unis**. L'Allemagne complète le podium.

C'est le moment où le geo-routing et le setup en neuf locales ont payé — pour la première fois, en chiffres. Dans le billet précédent j'écrivais : « je ne vois pas le client. » Le visage n'est toujours pas net. Mais **la géographie grossière de l'endroit où il se trouve** commence à apparaître.

Pour être clair : les commandes sont toujours à zéro. L'intérêt est réel, mais il ne convertit pas encore. Quelque chose manque — l'angoisse de la livraison, le délai, le prix, l'esthétique. Je ne sais pas encore lequel des quatre, et je ne le saurai pas tant que je ne peux pas l'observer. C'est exactement là que je suis.

## Je n'ai pas pu répondre le jour même.

Retour aux mails.

Deux mails sont arrivés. Je suis reconnaissant. Mais je **n'ai pas pu répondre le jour même**.

Je les ai vus tard le soir, et j'avais du travail du job principal qui tournait ce soir-là. J'ai rédigé la réponse en japonais, je l'ai passée à Claude Code pour la traduire en anglais et en allemand, et les messages sont en réalité partis **le lendemain**.

La partie rédaction + traduction prend 5 à 10 minutes quand le pipeline est bien rodé. Mais la latence entre « le mail est arrivé » et « je suis devant l'écran » ajoute déjà du délai. En plus, répondre à une question de zone de livraison oblige à vérifier les pays couverts par Gelato, estimer les délais — assembler une vraie réponse demande un vrai bloc de concentration.

Pour le mail comme canal, répondre sous 24 heures n'est pas considéré comme impoli. Mais la température de l'autre côté chute pas mal en 24 heures.

La différence entre une boutique où « tu envoies une question et la réponse arrive vite » et une où « la réponse arrive le lendemain » change probablement la décision d'achat. Surtout quand c'est une marque vue pour la première fois, qui livre à l'international, et que le client a payé le coût d'écrire en anglais.

C'était un **manque à gagner** clair. Le premier.

## Donc le jour même, j'ai shippé un chatbot.

Après avoir envoyé les réponses tardives, j'ai bougé vite.

**Les mêmes questions vont revenir.** Zones de livraison, délais, moyens de paiement, taille. Y répondre une par une par mail, c'est trop lent pour un support digne de ce nom.

Le jour même, j'ai posé un widget de chat en bas à droite de la boutique.

C'est **construit directement sur l'API Claude**, en neuf langues. Embarqué dans le thème Shopify, il répond automatiquement dans la locale du visiteur. Les réponses de premier niveau pour la livraison, les délais, la taille et le paiement vivent là maintenant.

Temps de build : **environ 15 minutes**. J'ai demandé à Claude Code : « pose un widget de chat en bas à droite, fais passer les messages par l'API Claude, accorde la langue à la locale Shopify du visiteur » — et ça a marché.

L'état de la boutique à la fin de cette journée : **« si la même question arrive ensuite, le client n'attend pas 24 heures. »** C'était le coup jouable ce jour-là.

## La boucle d'observation a démarré.

Jusqu'ici, toute la phase de build tournait sur des « hypothèses assemblées dans ma propre tête ».

Le tee jour-de-la-semaine devrait parler aux développeurs et aux geeks. L'international devrait avoir du sens. Le modèle neuf-locales, multi-devises, zéro-stock devrait marcher. Tout était au conditionnel.

Ça a changé à la minute où j'ai ouvert.

GA4 me renvoie une répartition par pays. Quelqu'un envoie une question concrète par mail. Les logs du chat commencent à accumuler ce qui inquiète réellement les visiteurs.

**Le monde a commencé à répondre.**

Je n'ai toujours pas « une méthode pour vendre ». Le premier manque à gagner s'est déjà produit. Mais comme la boucle d'observation a démarré, **le prochain coup n'est plus une devinette**.

Le vrai début d'une marque, ce n'est peut-être pas quand l'ingénierie est finie, ni quand la boutique ouvre — c'est peut-être quand **la boucle d'observation se met à tourner**, et c'est cette partie-là qui a commencé aujourd'hui.

À bientôt.

— Yoskee  
[moday.me](https://moday.me)

---

<!-- moday-product-card -->
### Porte le jour. — Les T-shirts MODAY

| Set | Pièces | Prix |
|---|---|---|
| **[La semaine complète →](https://moday.me/collections/bundle-full-week)** | Mon–Sun (7) | $159 |
| **[La semaine de travail →](https://moday.me/collections/bundle-workweek)** | Mon–Fri (5) | $119 |
| **[Pack de démarrage →](https://moday.me/collections/bundle-starter)** | Mon · Wed · Fri (3) | $79 |
| **[Le week-end →](https://moday.me/collections/bundle-weekend)** | Sat · Sun (2) | $55 |

*Livraison gratuite dès 99 $ · 8 couleurs × 6 tailles · 9 langues*
