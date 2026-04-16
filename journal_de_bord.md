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

