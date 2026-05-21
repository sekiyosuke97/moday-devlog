<!-- canonical: https://moday.me/blogs/journal/15min-chatbot-render-comeback -->

# Un chatbot monté en 15 minutes — j'avais lâché Render, et je l'ai repris

## Du manque à gagner du 19/05 à un truc qui tourne en 15 minutes

J'en ai parlé dans un autre billet : le 19/05, j'ai reçu mes deux premières demandes clients.
Je n'ai pas pu répondre dans la journée, mes réponses sont parties le lendemain.
J'ai pris ça pour ce que c'est — **du manque à gagner** — alors le jour même, j'ai monté un chatbot.

Ce petit widget classique dans le coin en bas à droite de la boutique.
Du début du chantier au moment où c'est déployé sur Shopify et où ça tourne : environ 15 minutes.
Je vais expliquer ce qu'il y a dedans, dans la limite de ce que j'en sais.

## L'architecture

En gros, ça donne ça.

- **Front** : un widget en bas à droite, intégré au thème Shopify (la manière exacte dont c'est implémenté, je ne la connais pas)
- **Backend** : sur Render.com, qui tape l'API Claude
- **Langue** : couplée à la locale Shopify, 9 langues
- **Historique** : sauvegardé dans un Google Sheet
- **Escalade** : les questions auxquelles il ne sait pas répondre redirigent vers le formulaire de contact

Le principe de conception est simple : **rester simple**, point.
À l'échelle d'une activité individuelle, peu importe ce qu'on fait, je ne veux pas trimballer de complexité.

## J'avais lâché Render, et je l'ai repris

Dans un autre billet, j'avais annoncé que « **FastAPI / Render, c'est terminé** ».
C'est contradictoire en apparence, mais ce que j'ai retiré, c'était l'usage **Webhook**.
Le traitement qui reçoit les commandes Shopify et les pousse vers Gelato tournait sur un FastAPI hébergé sur Render.
Ça, je l'ai remplacé par une autre archi (un sujet à part entière — j'en ferai un billet une autre fois).

Le chatbot, lui, a **ressuscité Render dans une autre configuration**.
L'infra qui faisait tourner le serveur Webhook, et celle qui sert d'API au chatbot.
Deux rôles différents, deux services différents, deux process différents.
Le seul point commun, c'est que c'est Render des deux côtés.

« J'ai lâché Render » et « j'utilise Render » ne se contredisent pas.
C'est juste **rechoisir le meilleur outil à l'instant T, en fonction de l'usage**.
Se laisser enfermer par une décision passée — « je n'utiliserai plus jamais ça » — fige le jugement.

L'axe de décision, je le garde. L'implémentation, c'est Claude Code qui la pose.
À chaque fois qu'on rebâtit, on va chercher l'optimum du moment.

## L'historique part dans un Google Sheet

Tous les échanges entre le bot et les utilisateurs partent dans un Google Sheet.
Date, locale, question de l'utilisateur, réponse du bot, escalade ou pas.

C'est une proposition de Claude Code que j'ai retenue.
Avec le recul, ça tombait juste pour trois raisons.

1. **Pas envie de monter une base de données** : il faut concevoir le schéma, il y a un coût d'exploitation, il faut aussi de quoi visualiser. À l'échelle d'une activité individuelle, c'est lourd
2. **Ça ne coûte rien** : un compte Google et c'est gratuit
3. **Quand je voudrai analyser plus tard, Claude Code comme moi pourrons lire directement** : il suffit de regarder les colonnes pour tout comprendre

Le troisième point compte beaucoup.
Quand je demanderai à Claude Code « **fais-moi une synthèse des demandes récentes** »,
il pourra aller lire le Sheet directement.
Avec une base de données, il faut écrire un script d'extraction, sortir un CSV — une étape de plus à chaque fois.

Une vraie base, ce serait plus propre, mais à l'échelle actuelle, le Sheet suffit largement.
À cette phase, c'est de la **bonne flemme**, je pense.

## La gestion des 9 langues

On récupère la locale active sur Shopify et on la passe au bot.
Le bot tape l'API Claude avec un prompt qui dit « **réponds dans cette langue, s'il te plaît** ».
Aucune étape de traduction au milieu. Claude écrit directement dans la langue cible.

Dans un autre billet, j'ai écrit « pas de la traduction, mais de la localisation-réécriture » — ça vaut aussi pour le bot.
On n'écrit pas en japonais qu'on traduit ensuite en français : dès le départ, la réponse sort dans un registre de natif français.
Pour l'allemand, c'est un natif allemand qui répond.
Tout se passe dans le modèle, donc on supprime structurellement la latence de traduction et le risque de contresens.

Là encore, rien d'extraordinaire.
J'ai juste demandé en une ligne : « **prends la locale Shopify et réponds dans cette langue** ».

## Dans le prompt, j'ai écrit « connais le site »

Le bot sait répondre sur les infos présentes sur le site MODAY et sur les données produits Gelato.
Zones de livraison, délais, tailles, moyens de paiement, politique de retour, prix, composition des bundles.

J'ai demandé à Claude Code de « **connaître** » tout ça.

Pour être honnête, **comment il s'y est pris pour les connaître, je n'en sais rien**.
Est-ce que c'est encodé dans le prompt, est-ce qu'il fetch le site,
est-ce que c'est un mix des deux — c'est Claude Code qui a tranché et implémenté.

Comme je l'ai écrit ailleurs : j'ai donné l'instruction, j'ai laissé l'implémentation.
Ça tourne, les réponses qui sortent sont propres, donc pour l'instant ça me va.
Quand ça cassera, je dirai à Claude Code « répare ».

## Ce qui n'a pas de réponse part vers le formulaire de contact

Laisser le bot répondre à toutes les questions, c'est dangereux.

Conseil taille sur un cas particulier, emballage cadeau, demandes B2B, gestion d'incident.
Si le bot affirme quelque chose sur ces sujets, ça finit par produire des malentendus.

Quand le bot estime que « ce n'est pas à moi de répondre », il redirige vers le formulaire de contact.
Le design des garde-fous, je l'ai aussi confié à Claude Code.
Tout ce que j'ai fait, c'est demander en une ligne : « **mets en place que les questions sans réponse renvoient vers le formulaire de contact** ».

Quelles questions le bot prend en charge, lesquelles il escalade.
C'est Claude Code qui a tracé la frontière.
J'ai prévu de regarder les logs de temps en temps et de corriger si un aiguillage est manifestement faux,
mais pour l'instant il n'y a rien à corriger.

Si ça a tenu en 15 minutes, c'est parce que dans ces 15 minutes il y avait peu de décisions à prendre.

« En bas à droite », « base API Claude », « 9 langues », « Render réactivé », « historique dans un Sheet »,
« escalade vers le formulaire de contact ».
Une fois ces choix posés, c'est Claude Code qui assemble.
Moi, je donne le GO et je vérifie que ça tourne.

Deux jours après l'ouverture de la boutique, le socle d'automatisation du support s'est mis en route.
La règle « **une amélioration par jour** » : c'était la première.

À très vite.

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
