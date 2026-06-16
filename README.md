# Destinations Quizz

Prototype d'un quiz **psychographique** de recommandation de destinations de voyage.
On quitte le matching de tags (« plage ou montagne ? ») pour placer l'utilisateur **et** les destinations dans un même espace vectoriel à 5–6 axes, et recommander par similarité cosinus.

Travail exploratoire — note de cadrage, prototype web et simulation de robustesse du scoring.

## Idée

Au lieu d'additionner des préférences déclarées, on **infère un profil de voyageur** sur quelques axes psychographiques :

1. Nouveauté ↔ Familiarité
2. Action ↔ Ressourcement
3. Culture / profondeur ↔ Hédonisme
4. Animation urbaine ↔ Nature / calme
5. Confort / standing ↔ Authenticité locale
6. *(optionnel)* Structure ↔ Spontanéité

Chaque destination est scorée sur les mêmes axes. La recommandation devient un **plus proches voisins** dans cet espace.

Voir [`quiz-psychographique-note-cadrage.md`](./quiz-psychographique-note-cadrage.md) pour le raisonnement complet (constat, leviers, mécaniques, pièges).

## Structure du repo

```
.
├── quiz-psychographique-note-cadrage.md   Note de cadrage / réflexion
├── quiz_destination.ipynb                 Notebook : scoring villes, simulation Monte Carlo
└── quiz_web/
    ├── index.html                         Quiz interactif (front statique)
    └── stats.html                         Dashboard des stats de simulation
```

### `quiz_web/index.html`
Quiz web autonome (HTML + CSS + JS, sans build). Pose une série de questions organisées en **blocs thématiques**, agrège les réponses en un vecteur utilisateur, puis affiche les destinations les plus proches.

Ouvrir le fichier directement dans un navigateur :
```bash
open quiz_web/index.html
```

### `quiz_web/stats.html`
Tableau de bord des probabilités d'apparition en **Top 3** par ville et par couloir (proche / Europe / monde, patrimoine / nature / urbain). Basé sur une simulation Monte Carlo de **30 000 profils aléatoires × 9 couloirs**, en *hard filter*.

### `quiz_destination.ipynb`
Notebook Jupyter :
- scoring des villes sur les axes psychographiques,
- génération de profils aléatoires,
- simulation Monte Carlo pour mesurer la robustesse et la diversité des recommandations,
- export des données utilisées par `stats.html`.

Mise en place d'un environnement local :
```bash
python3 -m venv quiz-venv
source quiz-venv/bin/activate
pip install jupyter pandas numpy
jupyter notebook quiz_destination.ipynb
```

> Le venv (`quiz-venv/`) est volontairement ignoré par git (`.gitignore`).

## État du projet

Prototype en cours d'itération. La V1 vise une mécanique simple : **blocs + agrégation par bloc, sans routage adaptatif**. Le branchement intelligent et l'ajustement des pondérations via les ~9 000 trips historiques viendront ensuite.

## Questions ouvertes

- Nombre d'axes définitif (5 ou 6) et priorité entre eux
- Découpage en blocs et nombre d'items par bloc (2 ou 3)
- Méthode de scoring des villes (manuel / dérivé POI / LLM / mix)
- Mécanique de quiz à privilégier (MaxDiff, branchement, choix visuel)
- Sortie : ville unique ou Top 3 avec explication

Détails dans la note de cadrage, §9.
