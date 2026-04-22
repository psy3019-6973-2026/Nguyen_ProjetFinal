# Journal de bord
Ce document sert à sauvegarder les étapes, les questionnements ou des remarques en cours de route lorsque j'effectue les tâches du projet

## 15 avril 2026 – 21h à 22h30

Utilisation du ficher yml du cours de visualisation au début (à confirmer si c’est pour le reste des étapes)

Téléchargement des 40 participants (et non 30)
Ajout du directory pour le téléchargement des données, fait qu’il y a une copie dans le git que je peux push + pas besoin de le retélécharger à chaque fois que je run le code si les données sont déjà téléchargées.

Choses à rajouter dans notebook (utiliser pour préparer les données) ou code pour classificateur (pour l’entraînement des modèles, pourrais peut-être être directement fait dans le notebook, à déterminer)
-	Ajouter une normalisation (StandardScaler)
-	Faire une validation croisée
-	Comparer avec et sans PCA ou feature selection? (pas présent dans le projet original)

Inscription au NITRC et exploration des fichiers training set phenotypic et testing set phenotypic


## 16 avril – 12h 
Il y a seulement 30 participants qui ont des données phénotypiques --> explique pourquoi le projet initial a juste fait son projet avec 30 participants

Lorsqu’on vérifie les diagnostics de tdah, il y a 17 contrôles et 13 adhd, par contre dans le projet original c’était l’inverse  à vérifier si l’identification des données a changé.
Même problème avec la distribution de l'âge, ce n'est pas la même chose que le projet original --> peut-être que les données ont étés changées/updater depuis le projet original (à vérifier)

La matrice de corrélation age-adhd ne sert à rien (que les diagonales), ne démontre pas d’informations utile et il va avoir une visualisation avec matrice de corrélation plus tard.

PROBLÈME: ce n'est pas que seulement 30 participants a des données phénotypes mais lorsqu'on fait data.phenotypic() nilearn a un problème et ne va chercher que 30 participants (et ce n'est pas les même 30 participants que le projet initial, ce qui explique la différence dans les distributions d'âge et de tdah entre le projet original et mon projet)

## Travail du 21-22 avril
Visualisation avec le interactive scatter plot:
- Contrairement au projet original, l'utilisation de son code ne montre pas les participants qui n'ont pas de valeur au full_4_iq (notre graphique présente 22 participants de moins). Je préfère cette visualisation que l'original qui met un peu arbitrairement les données manquantes au milieu du graphique, induisant un peu en erreur l'interprétation de la figure

Visualisation de l'extraction des features:
- Il semble avoir eu un changement dans la valeur par défaut pour le cmap. Le projet original avait cmap = 'cold_hot' sans la mentionner directement dans le code tandis que la valeur par défaut dans la présente version de nilearn est 'RdBu_r'

Import de l'atlas:
- Avec le présente version de nilearn, on doit maintenant préciser quelle résolution on veut lorsqu'on fetch l'atlas, semble qu'ancienne version retournait toutes les versions en même temps. Les keys ont également changer, donc on doit faire parcellations.maps pour avoir le file_name de l'atlas

ConnectivityMeasure:
- Il y a de l'incohérence dans le projet original. Il initialise une mesure de corrélation qui enlève la diagonale et vectorize = True donc garde seulement le triangle inférieur + flatten puis retourne un array de 1D. Par contre, dans la boucle pour faire la matrice de corrélation pour tous les sujets, on reinitialise la mesure de corrélation sans enlever la diagonale et avec vectorize = False ce qui retourne un array de 2D. L'array de 2D est utiliser pour les visualisations par la suite, mais utiliser ce type d'array donne de l'information qui est redondante pour les modèles de classifications.
- Pour mon projet, je préfère donc utiliser la mesure de connectivité sans la diagonale et avec seulement le triangle inférieur puisque le but principal de ce projet est les classificateurs. Par contre, je vais utiliser la méthode discard_diagonal = False et vectorize = False pour faire les mêmes visualisations que le projet original (mais cette méthode n'est pas utiliser pour les classificateur)

Ajout de XGBoost dans l'environnement du cours de visualisation pour faire les classifications

Classifacteurs
- au lieu de faire les classifications dans un autre code, je les ai fait directement dans le même notebook où on a préparer les données afin de ne pas à avoir redownload les données préparées
- aucune autre modification a été fait au code pour les classifications 



