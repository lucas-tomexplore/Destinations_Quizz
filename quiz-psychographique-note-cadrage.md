# Faire évoluer le quiz de destination : note de cadrage

*Base de réflexion — pour Emery*

## 1. Le constat de départ

Notre quiz actuel aide l'utilisateur à trouver sa destination, mais son approche est **linéaire** : chaque question est indépendante (« plage ou montagne ? », « budget ? », « actif ou repos ? »), on additionne des préférences déclarées, puis on fait correspondre ces préférences à des étiquettes (tags) posées sur nos villes.

Trois limites à cette approche :

- **C'est additif.** On traite les préférences comme des briques séparées, alors qu'elles forment en réalité une *personnalité de voyageur* cohérente.
- **C'est déclaratif.** Les gens se connaissent mal et répondent ce qui est socialement désirable : tout le monde coche « culture » et « aventure ».
- **C'est plat.** La question N+1 ne dépend jamais de la réponse N. On pose donc beaucoup de questions pour peu de signal réel.

L'objectif de cette réflexion : passer d'un quiz qui *additionne des goûts* à un quiz qui *infère un profil* et le rapproche des destinations qui lui correspondent.

## 2. Deux leviers à distinguer

On confond souvent deux choses qu'il faut traiter séparément :

- **Ce qu'on mesure** → le cadre psychographique (quelles dimensions psychologiques décrivent un voyageur).
- **Comment on le mesure** → la mécanique du quiz (le format des questions).

Notre quiz actuel est faible sur les deux. On peut progresser sur chacun indépendamment.

## 3. Levier A — Ce qu'on mesure : les psychographies

Plutôt que d'interroger des *caractéristiques* (plage/montagne), on infère des *traits psychologiques*. Quelques cadres de référence utiles, à connaître sans forcément tout appliquer :

- **Modèle de Plog** (le classique en tourisme) : il place les voyageurs sur un continuum **psychocentrique ↔ allocentrique**. Les psychocentriques cherchent le familier, le rassurant, le packagé ; les allocentriques cherchent la nouveauté, l'exotique, l'indépendance. La majorité des gens sont au milieu. Point intéressant pour nous : ce même axe sert à la fois à profiler l'utilisateur **et** à positionner nos villes (une destination « se découvre » par les allocentriques puis se mainstreamise).
- **Big Five / OCEAN** : l'ouverture à l'expérience corrèle très fort avec la recherche de nouveauté. Un seul trait psychologique donne déjà beaucoup d'information.
- **Push / pull theory** : ce qui *pousse* à partir (besoin de déconnecter, de découvrir, de fêter) vs ce qui *attire* vers un lieu précis.

### Proposition de point de départ : 5-6 axes pour nos villes européennes

À débattre, mais voici une grille cohérente avec nos données (citybreaks européens, 50 villes, 35 000 POI) :

1. **Nouveauté ↔ Familiarité** — appétence pour l'inconnu vs le rassurant.
2. **Action ↔ Ressourcement** — rythme intense, exploration vs détente, lâcher-prise.
3. **Culture/profondeur ↔ Hédonisme** — patrimoine, musées vs food, fête, plaisir.
4. **Animation urbaine ↔ Nature/calme** — buzz de la ville vs échappée verte.
5. **Confort/standing ↔ Authenticité locale** — premium, lisse vs immersion, local.
6. *(optionnel)* **Structure ↔ Spontanéité** — tout planifié vs improvisation.

Avantage : ces axes sont en grande partie **dérivables de nos POI**. La densité musées / restaurants / vie nocturne / espaces verts d'une ville donne déjà un scoring « gratuit » sur plusieurs axes.

## 4. Structurer en blocs thématiques

Plutôt qu'une liste plate de questions, on regroupe les questions en **blocs thématiques**, chaque bloc correspondant à un axe psychographique du §3. Ce n'est pas qu'une question d'organisation : il y a une vraie raison de fond.

**La raison profonde (mesure).** En psychométrie, on ne mesure jamais un trait avec une seule question : une question isolée est bruitée (humeur, interprétation du mot, contexte). La bonne pratique est de poser **2-3 items qui triangulent la même dimension**, puis de les agréger en un score de bloc, beaucoup plus stable. Autrement dit, chaque bloc *est l'instrument de mesure d'un axe*. Le « bloc Rythme » ne pose pas une question sur le rythme — il en pose deux ou trois dont la combinaison donne une coordonnée fiable sur l'axe *Action ↔ Ressourcement*. C'est exactement comme ça qu'on construit un vecteur robuste (cf. §6) au lieu d'un empilement de réponses fragiles.

**La raison pratique (modularité).** Les blocs sont des modules réutilisables : on peut les réordonner, en ajouter, en retirer, les A/B tester ou les traduire sans toucher au reste.

### Ce que veut dire « bloc intelligent »

Deux niveaux, et c'est là qu'on quitte définitivement le linéaire :

- **À l'intérieur d'un bloc** : les réponses ne vivent pas isolées. Elles s'agrègent en un sous-score, et peuvent se contrôler entre elles (si deux items d'un même bloc se contredisent, on sait que le signal est incertain).
- **Entre les blocs** : on fait du routage au niveau du *bloc*, pas de la question. Si un bloc révèle déjà une tendance nette avec une bonne confiance, on peut alléger ou sauter un bloc devenu redondant, et **réinvestir le budget de questions là où le profil est encore flou**. C'est l'inverse d'un quiz qui déroule toujours la même séquence.

### Mise en garde pour la V1

Commencer **simple**. La première version peut très bien être « blocs + agrégation par bloc », *sans* routage adaptatif. Le routage intelligent (sauter / pondérer des blocs) est une couche à ajouter **ensuite**, une fois les blocs et le scoring validés sur de la vraie donnée. Sinon on se complexifie la vie avant d'avoir prouvé que la grille fonctionne.

## 5. Levier B — Comment on le mesure : sortir du linéaire

Quatre mécaniques qui densifient le signal au lieu de le diluer :

- **Branchement adaptatif** : la question suivante dépend des précédentes. On maximise l'information par question (un simple arbre de décision suffit pour démarrer, pas besoin de modèle complexe).
- **Arbitrages forcés / MaxDiff** : au lieu de « note ton intérêt pour X », on force « lequel de ces deux séjours te tente le plus ? ». Ça tue le biais « tout le monde dit oui » et révèle les vraies priorités.
- **Scénarios projectifs** : « C'est le jour 3, tu as un après-midi libre, tu fais quoi ? » — capte l'implicite bien mieux qu'une question directe.
- **Préférence visuelle** : montrer des images, faire choisir. Très efficace pour le voyage, où l'émotionnel et l'esthétique se verbalisent mal.

## 6. Le cœur du système : un espace partagé

L'idée structurante : on arrête le matching de tags, et on place **l'utilisateur ET les destinations dans le même espace psychographique** (un vecteur de 5-6 dimensions). La recommandation devient alors une simple recherche des **plus proches voisins** (distance / similarité cosinus).

C'est ce qui résout le côté « linéaire » : on n'a plus besoin que l'utilisateur coche explicitement « j'aime la nouveauté » — on l'infère de ses réponses, et on peut pondérer chaque dimension.

Concrètement :

1. On score nos villes une fois sur les 5-6 axes (à la main au début, puis affiné via les POI ou un LLM en batch).
2. Le quiz produit un vecteur utilisateur.
3. On calcule la similarité — trivial côté client ou en Cloud Function.

## 7. Le piège à éviter

**Plus sophistiqué ≠ meilleure UX.** L'erreur serait d'allonger le quiz. Tout l'enjeu est d'extraire **un maximum de signal en 5 à 7 questions**. C'est exactement pour ça que le MaxDiff et le branchement adaptatif sont intéressants.

## 8. Atout maison : on a déjà de la donnée

3 500 utilisateurs et ~9 000 trips créés : c'est une mine pour **calibrer et valider** la grille. On peut vérifier a posteriori si nos axes prédisent bien les villes réellement choisies, et ajuster les pondérations en conséquence. À ne pas négliger dans la réflexion.

## 9. Questions ouvertes à trancher

- Combien d'axes retient-on (5 ou 6) ? Lesquels sont prioritaires ?
- Quel découpage en blocs, et combien d'items par bloc (2 ou 3) ?
- Comment score-t-on les 50 villes : manuel, dérivé des POI, LLM, ou un mix ?
- Quelle mécanique de quiz privilégier (MaxDiff, branchement, visuel — ou combinaison) ?
- Combien de questions maximum ? (cible : 5-7)
- Sortie attendue : une ville unique, ou un top 3 avec une explication du « pourquoi cette ville te correspond » ?
- Comment exploiter les 9 000 trips existants pour valider la grille ?

## 10. Premières étapes suggérées

1. **Figer les axes** (atelier court à partir de la grille du §3).
2. **Scorer 10 villes à la main** sur ces axes — assez pour tester la cohérence.
3. **Découper en blocs et rattacher chaque axe à 2-3 items**, en testant une mécanique non linéaire (sans routage adaptatif pour la V1).
4. **Prototyper le matching** (vecteur utilisateur → similarité cosinus → top 3).
5. **Tester sur quelques profils internes**, puis confronter aux trips réels.

---

*Cette note pose les bases d'une réflexion — elle n'est pas un cahier des charges. L'idée est de donner un cadre et des pistes, à challenger et préciser.*
