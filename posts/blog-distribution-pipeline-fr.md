<!-- canonical: https://moday.me/blogs/journal/blog-distribution-pipeline -->

# Un seul billet, neuf langues, dix plateformes : le pipeline de diffusion MODAY

## J'écris une fois en japonais, ça atterrit dans neuf langues sur dix endroits

Voici ce qui se passe quand je termine un brouillon japonais pour le devlog MODAY :

| Niveau | Destination |
|---|---|
| Possédé | Blog Shopify (JA + 8 locales) |
| Diffusion automatique par API | dev.to / Qiita / Zenn / GitHub devlog |
| Collage manuel, fichiers de handoff générés | note / Medium / Tumblr |

Côté écriture, tout le boulot tient en deux gestes : finir le brouillon, lancer `distribute.py` une fois. Le reste se déploie tout seul.

J'ai monté ce pipeline en trois jours et je le fais tourner sur chaque billet depuis le premier. Voici la forme réelle de la bête.

## La décision de design : séparer « auto » et « manuel » dès le départ

La première chose que j'ai tranchée, c'est de **scinder les cibles en deux niveaux**.

D'un côté, les plateformes avec une API d'écriture qui fonctionne (Shopify, dev.to, Qiita, Zenn-via-GitHub, GitHub lui-même). De l'autre, celles sans API ou avec une API hostile (note, Medium, Tumblr). Dès qu'on essaie d'unifier les deux, le script vire au marécage.

Donc :

- Niveau auto — `distribute.py` fait tout par HTTP
- Niveau manuel — `prepare_handoff.py` crache des **fichiers prêts à coller** qu'un humain porte jusqu'à l'UI

Le niveau manuel, c'est la partie que je n'ai pas encore réussi à confier à l'IA. Mais tout ce qui précède le geste de collage est automatisé.

## Ce que fait vraiment `distribute.py`

Le flux à l'intérieur de `distribute.py` :

1. **Hero gate au démarrage.** Si `content/posts/<slug>/hero.png` manque, le script s'arrête net. Pas d'image de couverture, pas de diffusion. C'est un garde-fou structurel contre le « oups j'ai oublié la hero ».
2. **Poster sur le Shopify Journal blog**, corps + hero en une fois.
3. **Enregistrer les traductions Shopify**. Lit les fichiers voisins `webhook/posts/<NNN>-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md` et envoie les huit locales d'un coup via l'API `translationsRegister`.
4. **POST vers dev.to**, corps EN, avec l'URL CDN Shopify réutilisée comme cover.
5. **POST vers Qiita**, corps JA avec `canonical_url` qui pointe vers Shopify.
6. **Zenn — pas d'appel API**. Zenn n'expose pas d'API d'écriture, donc j'ai configuré la sync Zenn ↔ GitHub. Un push publie un billet automatiquement.
7. **GitHub devlog** : commit de `<slug>-ja.md`, `<slug>-en.md`, `<slug>-hero.png` dans le repo `moday-devlog`.
8. **Appelle `prepare_handoff.py`** pour générer les fichiers de collage du niveau manuel.
9. **Écrit `status.json`** à côté de la source, en consignant URL / ID / timestamp pour chaque plateforme.

Les deux bouts dont je suis le plus content, c'est le **hero gate** et la **route Zenn-via-GitHub**. Le hero gate rend structurellement impossible d'expédier un billet sans image de couverture. Et Zenn — qui refuse délibérément d'exposer une API d'écriture — reçoit quand même le billet, parce qu'un `git push` suffit comme pont.

## Ce que fait `prepare_handoff.py`

Produit des fichiers prêts à coller pour les trois destinations manuelles :

| Fichier | Contenu | Langue |
|---|---|---|
| `note.md` | Original JA avec commentaires d'instructions de collage. Les tableaux sont convertis en paragraphes « **Label :** valeur » parce que note ne rend pas les tableaux Markdown. | JA |
| `medium.html` | Traduction EN en HTML. Bandeau d'instructions en haut avec CSS qui désactive la copie, corps en dessous. ⌘+A → ⌘+C ne copie que le corps. | EN |
| `tumblr.md` | Lede EN (H1 jusqu'au premier H2, plafonné dur à 1500 caractères) + lien canonical + bloc de tags style Tumblr. | EN |

Le détail non évident ici, c'est le **dialecte par plateforme**.

note ne rend pas les tableaux Markdown — colle le truc brut et tu te retrouves avec `| en-tête | valeur |` affiché en texte littéral, ce qui est moche. Donc `prepare_handoff.py` réécrit chaque tableau en paragraphes à label en gras.

Medium a le problème inverse : copier-coller depuis n'importe où traîne plein de métadonnées avec. Je voulais que le rédacteur (moi) puisse ⌘+A → ⌘+C la page et n'obtenir *que le corps*. Donc le HTML de sortie a un bandeau d'instructions en haut avec du CSS `user-select: none` — visible pour le rédacteur, invisible pour le presse-papiers.

La culture Tumblr ne récompense pas le fait de déverser un essai de 3000 mots dans un post. Donc j'extrais juste le lede et je renvoie vers le canonical.

Chaque plateforme reçoit son **dialecte et sa culture** respectés, à un seul endroit centralisé.

## Je laisse aussi l'IA traduire — mais uniquement dans la sous-cription

Tout le pitch de MODAY, c'est « une marque construite par l'IA », donc évidemment la traduction passe aussi à l'IA. J'ai changé le « comment », récemment.

- Avant : `distribute.py` appelait l'API Anthropic avec Claude Haiku pour chaque locale.
- Maintenant : je demande directement à Claude Code (Opus 4.7) de « réécrire ça pour huit locales », en session.

La raison est bête et peu sexy : **je ne veux pas d'une seconde facture au compteur**. Je paie déjà Claude Max. Tout ce qui peut se passer à l'intérieur de cet abonnement doit s'y passer.

C'est moins un arbitrage technique qu'une décision **business**. Pour une boutique à une personne, le plus important, c'est de tenir les coûts fixes au plus bas. Faire tourner un abonnement Claude Max *et* une facture Anthropic au compteur sur la même tâche, c'est une façon brouillonne de gérer un P&L perso.

L'autre chose qui comptait : la **qualité**. Les sorties de Haiku via API se lisaient comme des traductions — exploitables, mais pas natives. Partir sur neuf locales, ça veut dire qu'il me faut des réécritures qui se lisent comme si un founder natif les avait écrites sur place. Sans ça, la marque ne prend sur aucun de ces marchés.

Ce genre de réécriture, ce n'est pas de la traduction ; c'est de la localisation-réécriture. La faire passer par Claude Code sur Opus 4.7 m'a donné un output nettement meilleur que l'ancien pipeline Haiku-API.

Couper le coût a en fait remonté la qualité. Je ne m'y attendais pas.

## Le quotidien réel

Le rythme opérationnel ressemble maintenant à ça :

1. Brouillonner un billet JA dans Claude mobile (en général dans le métro).
2. Dans une session Claude Code, le déposer à `webhook/posts/004-<slug>-ja.md`.
3. Demander à Claude Code de « réécrire pour huit locales » — il produit `webhook/posts/004-<slug>-{en,de,es,fr,it,ko,pt-BR,zh-CN}.md`.
4. Générer la hero avec `webhook/generate_hero.py` → `content/posts/<slug>/hero.png`.
5. Lancer `python webhook/distribute.py webhook/posts/004-<slug>-ja.md`.
   - Diffuse automatiquement vers Shopify (JA + 8 locales), dev.to, Qiita, GitHub.
   - Appelle `prepare_handoff.py` pour déposer `content/posts/<slug>/{note.md, medium.html, tumblr.md}`.
6. Ouvrir note / Medium / Tumblr dans un navigateur, coller les fichiers préparés.

Le seul moment où je *pense* vraiment, c'est l'étape 1. Le reste, c'est des instructions à Claude Code, un script qu'on lance, et du collage.

## De « j'ai eu une idée dans le métro » à « tout est en ligne », en une journée

La partie de ce truc que je préfère, ce n'est même pas le script — c'est le **flow côté humain**.

Les idées me tombent dessus loin d'un bureau. Dans les transports. Juste avant de dormir. En marchant quelque part. C'est là que j'ouvre Claude mobile, je sors le projet MODAY, et je débroussaille le billet à voix haute. Le temps que je rentre, le brouillon est quasi prêt.

Au bureau, j'ouvre Claude Code, je lui file le brouillon, il produit les réécritures locales et il fait tourner le pipeline.

Le temps que je passe *assis à un bureau à pousser des mots* est proche de zéro. C'est cette partie-là du « brand build piloté par l'IA » qui me semble vraiment réelle, en ce moment.

## Pour conclure

Le pipeline lui-même a aussi été écrit par Claude Code. J'ai juste dit « je veux un script qui diffuse vers neuf langues et dix plateformes », et on a affiné le cahier des charges en conversation.

Toujours sur la to-do : intégration de l'API Tumblr, une vue dashboard de `status.json`, fan-out automatique vers les réseaux sociaux. Je les replierai au fur et à mesure que la marque avance.

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
