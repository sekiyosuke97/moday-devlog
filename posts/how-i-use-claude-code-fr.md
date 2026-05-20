<!-- canonical: https://moday.me/blogs/journal/how-i-use-claude-code -->

# Comment j'utilise Claude Code — ne rien ranger, tout déléguer, y aller au feeling

## Petit retour en arrière : comment je m'en sers vraiment

J'ai écrit beaucoup sur la construction de MODAY, mais je n'avais jamais écrit sur **la façon dont je pilote Claude Code** au quotidien.

Le choix de la stack, l'assemblage du pipeline de publication, la localisation en neuf langues, le chatbot monté en 15 minutes — tout ça, c'était le côté « **ce que j'ai construit** ».

La boutique est ouverte, on est entrés dans la phase d'exploitation, alors c'est le bon moment pour prendre un peu de recul et écrire la version méta.

Conclusion en tête : **je ne range rien, je délègue, j'y vais au feeling.**

Ce sera probablement à contre-courant de la plupart des guides « comment utiliser Claude Code » que vous croisez.

## Le CLAUDE.md, c'est Claude qui l'a écrit

On vous dira : « **rangez bien les infos de votre projet dans CLAUDE.md** ». Identité de marque, stack technique, conventions de code, priorités. L'humain organise pour que Claude Code puisse attraper le contexte du projet. C'est l'usage standard.

Sur MODAY, **je n'ai écrit aucune ligne moi-même dans CLAUDE.md.** Je ne sais même pas exactement ce qu'il y a dedans.

Au début du build, j'ai dit à Claude Code : « tu peux ranger les fichiers toi-même si tu veux ». Il s'est mis à compiler tout seul l'identité de marque, la stack, les tables SKU, la configuration Shopify Markets, les priorités par phase. Quand j'y jette un œil de temps en temps, c'est probablement mieux foutu que ce que j'aurais fait à la main — et sûrement plus lisible pour Claude.

Du début à la fin, je n'ai jamais « rangé » quoi que ce soit. **Le geste de ranger lui-même, je l'ai passé du côté de Claude.**

## Les sessions, je les découpe au feeling

Je découpe en sessions, oui. Mais **sans règle**.

Pas de séparation stricte par objectif. C'est plutôt « contenu », « UI/UX », « MD (tâches diverses) » — des paquets larges. Génération d'images, traduction, code : tout peut se mélanger dans la même session.

Je ne sépare pas par rôle (« session traduction », « session code »). **Je sépare par flux de travail.** C'est grossier, mais ça produit un état où « les idées s'enchaînent toutes seules ».

Je suis en train de retoucher l'UI, et tout à coup : « ah, vu ce changement, il faudrait aussi ajuster les traductions ». Je lance la traduction dans la même session, sans transition. Comme le coût de porter le contexte d'une session à l'autre est nul, **le fil de mes décisions ne casse jamais**. C'est étonnamment efficace.

## Je donne quasiment aucune directive technique

Je l'ai écrit dans un autre billet : au moment du choix de la stack, je n'ai donné zéro contrainte technique. Uniquement des contraintes côté business. Cette posture n'a pas changé une fois passé en phase d'implémentation.

La seule chose que je rappelle explicitement, c'est :

« **Utilise Shopify et Gelato de manière standard, et garde l'implémentation custom au minimum.** »

C'est ma règle d'or sur les SaaS. À long terme, ce qui tient le mieux, c'est de rester dans le cadre prévu par l'éditeur. Le sur-mesure paraît séduisant à court terme, mais finit toujours par casser à la prochaine mise à jour. Flux standards, API standards, structure de thème standard. On en sort uniquement quand c'est vraiment nécessaire.

Avec juste ça en tête, je peux laisser à Claude Code la quasi-totalité des détails : appels d'API, stratégie de tests, gestion d'erreurs, mise en œuvre.

## « Tu peux me montrer ? » — « Non, débrouille-toi »

Claude Code me demande parfois confirmation. « Tu peux me montrer le contenu de ce fichier ? », « C'est bon comme ça ? », « Comment j'écris les tests ? ».

À presque toutes ces questions, je réponds : « **fais-le toi-même** ».

Tu veux voir un fichier, utilise ton outil de lecture. Tu attends une décision, prends-la toi-même. Résultat : la plupart du temps il va lire, il décide, il enchaîne directement avec l'implémentation.

C'est la mise en pratique de ce que j'ai écrit dans un autre billet : « **je veux passer l'initiative côté IA** ». Ne pas reprendre la décision, laisser la décision où elle est.

Au final, il ne reste que ce qui **ne peut absolument pas passer par une API**. Compte bancaire, validation des paiements, ouverture de comptes chez les prestataires, mise en facturation, création des clés API. Ces choses-là exigent un contrat avec un humain — c'est moi qui m'y colle. Tout le reste vit côté Claude.

## Faire patrouiller GA4 tous les jours, et exiger des propositions

Nouvelle routine, lancée depuis l'ouverture.

Tous les jours, je fais patrouiller Claude Code dans GA4, et je lui demande de **sortir des problèmes et des pistes d'amélioration**. Je regarde la liste, j'élimine seulement ce qui est manifestement à côté de la plaque. Les 60–70 % qui restent, je les fais implémenter dans la foulée.

Entre la proposition et l'implémentation, ma seule contribution, c'est un GO/NO-GO. Je n'écris pas de code, je ne pense pas l'architecture. Presque zéro.

Je vais en faire un principe d'exploitation : « **une amélioration mise en prod par jour, minimum** ». Que dès l'instant où la boutique est ouverte, chaque jour quelque chose s'améliore. Pari assumé : une marque dont la boucle d'amélioration ne s'arrête jamais finit par gagner.

Et 99 % de cette boucle d'amélioration, c'est Claude Code qui la fait tourner.

## Je ne range pas, et pourtant c'est rangé

En l'écrivant, je me rends compte que je ne fais quasiment aucun des gestes classiques du développement : « organiser », « concevoir », « planifier ».

CLAUDE.md, je ne l'écris pas. Les sessions, je les fais au feeling. Le workflow n'est pas routinisé. Pas de schéma d'architecture, pas d'outil de gestion de tâches. Et pourtant, du build à l'exploitation, ça tourne.

La vérité, c'est juste que **j'ai délégué le rangement à Claude**. Moi je ne le fais pas, mais Claude Code, lui, le fait. Donc dans les faits, l'état rangé est maintenu.

La configuration ressemble à celle de Masayoshi Son qui dit « on y va » et déclenche un commando d'exécution ultra-compétent qui se charge à la fois de l'organisation et de l'implémentation. **Je reste du côté de celui qui dit « on y va », et le commando d'exécution, c'est l'IA.**

Que l'on puisse, en tant qu'individu, reproduire cette configuration à l'ère de l'IA — c'est probablement le truc le plus marquant que j'ai senti en trois semaines.

## Pour conclure

Je ne pense pas que ce soit la « bonne » méthode. Il y a sûrement une approche tout aussi valable où l'on écrit un CLAUDE.md soigné, où l'on découpe ses sessions par objectif, où l'on routinise son workflow.

Dans mon cas, simplement, **ne pas ranger était plus rapide**. Si j'ai du temps à investir, je préfère le passer à juger ce que Claude Code sort plutôt qu'à organiser en amont.

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
