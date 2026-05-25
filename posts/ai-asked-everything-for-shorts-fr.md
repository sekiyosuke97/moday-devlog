<!-- canonical: https://moday.me/blogs/journal/ai-asked-everything-for-shorts -->

# Pour faire des shorts, j'ai demandé à l'IA absolument tout ce que je ne savais pas

## Je retire ce que j'ai dit sur « la boucle d'observation »

Dans un billet précédent, j'ai écrit que « la boucle d'observation avait démarré » — qu'à la seconde où la boutique a ouvert, le monde s'était mis à répondre.

Quatre ou cinq jours plus tard, voilà ce que j'ai vraiment compris : **l'échantillon est trop petit pour observer quoi que ce soit.**

Je peux fixer GA4, suivre les comportements de panier, éplucher les logs du chatbot — le volume est tellement bas que rien là-dedans ne produit une hypothèse exploitable. Pour seulement commencer à théoriser, il faut que plus de monde franchisse la porte.

Donc le bon coup ne s'appelle pas encore observation. Il s'appelle **faire monter le trafic d'abord**. J'avais l'ordre à l'envers.

## Il faut vraiment mettre les mains dans l'acquisition

Toute la phase de build, j'étais à fond sur **construire la machine**. Distribution neuf langues dix plateformes, chatbot automatisé, automatisation commande→production, boucle d'amélioration automatisée. Tout rangé sous « on construit le système, on laisse tourner ».

Je voulais que l'acquisition fonctionne pareil — budget pub qui rentre, la data s'empile, l'IA propose des améliorations, on automatise la boucle, terminé.

Sauf qu'il n'y a pas de budget pub là tout de suite (j'en ai parlé dans un autre billet). Avec le paid hors-jeu, **l'organique sur les réseaux est la seule voie qui reste**. Le short en particulier — pour un produit aussi visuel, le format devrait coller.

Un petit détail quand même : **je n'ai absolument aucune idée de ce qui marche en short en ce moment.**

Je ne regarde pas les shorts en français de manière suivie. Les shorts anglophones ? Encore moins. Je fais du conseil e-commerce comme métier principal, et là c'est une faiblesse que je dois assumer. Je mets les pieds sur un terrain qui n'est pas une force.

## Étape un : demander à Gemini

Je suivais les news Google I/O et je cherchais une occasion de pousser Gemini dans ses retranchements. Donc je lui ai posé : « Qu'est-ce qui cartonne en short vidéo pour un public business anglophone sur TikTok, LinkedIn et Shorts ? »

Ce qui est revenu, c'était un monde dont je ne savais rien :

- **Corporate Buzzword Satire** — des sketchs qui se moquent du vocabulaire vide du langage corporate : « Synergy », « Circle back », « Let's take this offline ».
- **« Day in the Life » version auto-ironique** — des trucs du genre « comment garder son Teams sur "Active" sans sortir du lit », qui rigolent du sentiment de rouage dans la machine.
- **Personnages type Corporate Erin** — des comédiens qui jouent la RH glaciale, sourire pro et débit rapide, qui emballe un licenciement dans une cadence joyeuse.
- **LinkedIn Lunatics** — des TikTokeurs qui lisent à voix haute et chambrent les posts business poétisés que les gens publient avec sérieux sur LinkedIn.

Le pattern que Gemini a tiré de là m'a frappé. Le fil rouge du buzz humour-business anglophone, c'est **« la mutinerie comique contre l'absurdité de la culture corporate »**.

C'est par définition un terrain adjacent à MODAY. L'univers d'un tee « MONDAY: System Booting... » et d'un tee « FRIDAY: Build Successful ✓ » vit à l'intérieur de cette même culture.

Il n'y a aucune chance que je tombe sur ces quatre genres en réfléchissant tout seul.

## Étape deux : passer le tout à Codex et lui demander un storyboard

J'ai filé le résultat Gemini directement à Codex. Prompt : « Écris le storyboard d'un short d'acquisition pour MODAY. 9:16 vertical, 22 secondes, public business anglophone, ton satire-et-humour, atterrissage sur la marque à la fin. »

Ce qui est revenu :

![Storyboard : Weekdays Ranked by Developer Damage](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-storyboard.png)

**« Weekdays Ranked by Developer Damage ».** Concept : classer les jours de la semaine selon les dégâts qu'ils infligent à un développeur. Pas un showcase produit — un **mème qui tient debout tout seul**. Conçu pour que les commentaires se mettent à se chamailler sur le classement, avec un « Tell me I'm wrong » en bout de course pour appâter. Et c'est seulement à la fin que la marque atterrit : « MODAY — Wear the day you survived. »

Le pitch produit est **planqué dans les deux dernières secondes**. La vidéo ne se lit pas comme une pub. Elle se consomme comme un mème. Les commentaires font le boulot. La stratégie d'acquisition, c'est littéralement le cœur de mon métier de consultant — et cette fois, je l'ai sous-traitée totalement à l'IA.

Et le résultat est nettement meilleur que ce que j'aurais ébauché moi-même.

## Étape trois : sortir quatre modèles réutilisables avec ChatGPT Image

Une série vidéo, ça a besoin de **personnages qu'on peut réutiliser**. Je n'ai pas les moyens d'embaucher des vraies personnes, et je n'ai pas le temps de tourner. ChatGPT Image 2.0 m'a généré quatre modèles d'un coup.

![Modèle 1](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-1.png)

![Modèle 2](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-2.png)

![Modèle 3](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-3.png)

![Modèle 4](https://raw.githubusercontent.com/sekiyosuke97/moday-devlog/main/posts/ai-asked-everything-for-shorts-model-4.png)

J'ai éclaté l'ethnicité, l'âge et le genre sur les quatre. Chacun garde une cohérence de vibe — côté ingénieur, côté télétravailleur, côté office-professional — mais les quatre ont une vraie tête différente.

Chaque modèle est arrivé avec angles de face, trois-quarts et profil, plus plusieurs expressions, tout ça depuis un seul prompt. C'est le casting récurrent de la série. **Quatre modèles maison, exclusifs à la marque.**

Louer un studio. Appeler une agence. Sourcer le vestiaire. Monter la lumière. Tout sauté. Coût quasi nul. Temps total, peut-être trente minutes.

## À partir d'ici, je bosse à la main

Les étapes qui restent :

1. Composer chaque scène en image fixe (modèle + tee + fond).
2. Animer l'image fixe en vidéo.
3. Ajouter SFX et sous-titres.
4. Poster sur TikTok / Instagram Reels / YouTube Shorts.

Pour ce tour, je pousse **le multi-langue et l'automatisation à l'étape suivante**. Une vidéo anglaise d'abord, faite à la main, lâchée dans la nature. Si ça touche, je scale le pattern gagnant sur les neuf langues et je monte la pipeline d'automatisation derrière. Si ça ne touche pas, j'essaie un autre angle.

C'est tout droit sorti du manuel du dev web : **construire un seul prototype qui marche à la main, n'investir dans l'automatisation qu'une fois qu'on voit la forme du gagnant.** L'acquisition suit la même règle.

## AI-driven, mais je reviens encore à mes propres mains

J'ai écrit dans un billet précédent : « passer tout ce qu'on peut à l'IA ». La doctrine n'a pas bougé. Cette fois encore, le storyboard, les modèles et la stratégie ont été montés par l'IA.

Mais **la composition et le montage de la première vidéo, je les fais à la main**. Pas parce que l'IA ne saurait pas techniquement. Parce que **je veux la texture du premier tour dans mes propres mains**.

Ce qui accroche. Où les spectateurs décrochent. Ce que la section commentaires fabrique. Je ne peux pas construire le critère de jugement pour la phase d'automatisation tant que je ne l'observe pas moi-même. Le faire à la main. Toucher, rater, consigner l'expérience — c'est **la matière brute du critère** dont j'aurai besoin plus tard.

La marque est AI-driven, mais **le jugement reste le mien**. Quand déléguer, quand pas — cette frontière, c'est le boulot du founder. Et là tout de suite, c'est un moment « on le fait à la main ».

Pour les curieux, voici la première vidéo :

[Instagram — MODAY: Weekdays Ranked by Developer Damage](https://www.instagram.com/p/DYurYaJCgqV/)

Est-ce que la première touchera ou se plantera, je ne sais pas encore. Touche → automatisation. Plante → autre angle. Dans tous les cas, une nouvelle boucle part d'ici.

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
