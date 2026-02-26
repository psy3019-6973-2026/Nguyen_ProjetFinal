# Projet final - PSY 3019

## Projet initial - [ADHD diagnosis prediction using machine learning de Iangola Andrianarison](https://school-brainhack.github.io/project/adhd-prediction/)
Objectif du projet: Entrainer des modèles de classifications sur des données IRMf pour prédire des diagnostics de trouble du déficit de l'attention avec ou sans hyperactivité (TDAH)

Le projet initial est effectué avec une base de données accessible avec Nilearn, le Nitric ADHD resting-state. L'auteure a seulement utilisé un sous-ensemble de la base de données (30 participants, 13 ADHD, 17 contrôle) et celui-ci est déjà pré-processed.

Plusieurs modèles de comparaisons ont étés effectués (KNN, Régression logistique, Arbre de décision, Random Forest, Machine à vecteurs de support (SVM) et XGBoost) et leur performance ont été mesurée par F1 score et l'accuracy


## Intérêt personnel
Je suis tout d'abord intéresser à apprendre à entraîner des modèles de classificateur, élément beaucoup mentionné durant mon parcours au baccalauréat mais dont je n'ai malheureusement pas eu la chance d'appliquer pratiquement. 

De plus, le TDAH est un sujet qui m'intéresse puisqu'il m'affecte personnellement (je suis TDA) et il semble également être un souci au niveau de la santé publique au Québec. 
Dans un système de santé où il semble avoir un manque perpetuel de temps, une méthode quantitative robuste et relativement rapide (comparativement à une liste d'attente pour voir un neuropsychologue) serait intéressante. 

## Description des tâches
### Tâche 1: Reproduire le projet intial (notebook) à partir d’un environnement vierge et documenter le processus
Le projet initial mentionne qu'une de ses limites est la petite taille de sa base de données. Or, seulement 30 des 40 participants disponibles n'ont été utilisé. 
Je vais donc tenter de refaire le projet, mais avec l'entierté de la base de données.

**Documentation du processus (changements potentiels en cours de route):**
- Temps total nécessaire pour réaliser le projet
- Bugs rencontrés et solutions
- Vérification de la reproductibilité (points forts et points faibles)
- Différences du processus et des résultats avec les 10 nouveaux participants

### Tâche 2: Adapter une analyse existante à un jeu de données ouvert différent
Après avoir assuré du bon fonctionnement du code et apporté les modifications nécessaires, je vais tenter d'entraîner des modèles de classificateurs sur un plus grand ensemble de données. 

*Si cette tâche s'avère plus demandante que prévue (excède 10h de travail, je vais entraîner moins de modèles de classificateur que le projet initial.*


Adapter une analyse existante à un jeu de données ouvert différent —> nilearn a seulement 40 participants d’un jeu de données qui a été pre-processed dans le contexte d’un concours. Donc checquer prendre quelle base de données pcq plusieurs initiatives et ensuite faire les analyses du projet initiale 

https://www.nitrc.org/frs/?group_id=383 

### Tâche 3: Ajouter une visualisation pertinente des résultats
Avec la nouvelle base de données qui est plus grande, 


explorer de nouvelles visualisation et de façon d'évaluer la performance

Ajouter une visualisation pertinente des résultats —> avec la nouvelle base de données qui est plus grande, refaire les graphiques présentées + proposer d’autres visualisations pertinentes qui n’étaient pas possible avec le base de données nilearn
Ou utiliser des classifiers différents
