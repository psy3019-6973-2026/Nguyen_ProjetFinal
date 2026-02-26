# Projet final - PSY 3019

## Projet initial - [ADHD diagnosis prediction using machine learning de Iangola Andrianarison](https://school-brainhack.github.io/project/adhd-prediction/)
**Objectif du projet:**
Entrainer des modèles de classifications sur des données IRMf pour prédire des diagnostics de trouble du déficit de l'attention avec ou sans hyperactivité (TDAH)

Le projet initial est effectué avec une base de données accessible avec Nilearn, le Nitric ADHD resting-state. L'auteure a seulement utilisé un sous-ensemble de la base de données (30 participants, 13 ADHD, 17 contrôle) et celui-ci est déjà pré-processed.

Plusieurs modèles de comparaisons ont étés effectués (KNN, Régression logistique, Arbre de décision, Random Forest, Machine à vecteurs de support (SVM) et XGBoost) et leur performance ont été évalué par F1 score, accuracy et matrices de confusions.


## Intérêt personnel
Je suis tout d'abord intéresser à apprendre à entraîner des modèles de classificateur, élément beaucoup mentionné durant mon parcours au baccalauréat mais dont je n'ai malheureusement pas eu la chance d'appliquer pratiquement. 

De plus, le TDAH est un sujet qui m'intéresse puisqu'il m'affecte personnellement (je suis TDA) et il semble également être un souci au niveau de la santé publique au Québec. 

**Faits saillants:**
- Autour de 14 % des Québécois de 10 à 17 ans consommaient des psychostimulants spécifiques au TDAH en 2017. (ce qu'on devrait observer: 2-5 %)
- Prévalence du TDAH chez les Québécois de moins de 25 ans: 6,4 % VS 2,4 % chez les autres jeunes Canadiens.
- Une évaluation neuropsychologique requiert généralement de quatre à huit heures d’entretiens, en une ou plusieurs séances MAIS plusieurs ont eu leur diagnostic en une rencontre virtuelle de 60 minutes. --> risque de perte de précision dans le diagnostic

*[Article de journal pour les intéressés](https://www.lapresse.ca/actualites/sante/telemedecine/60-minutes-pour-un-diagnostic-de-tdah/2024-11-20/il-risque-d-y-avoir-une-perte-de-precision-dans-le-diagnostic.php)*

Dans un système de santé où il semble avoir un manque perpetuel de temps et de ressource, une méthode quantitative robuste et qui serait probablement plus rapide qu'une consultation en neuropsychologie serait intéressante pour complémenter l'application actuelle dans l'évaluation de TDAH. 

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

Le dataset disponible sur Nilearn est en fait un sous-ensemble d'un plus gros dataset, le ADHD200. Dans le cadre d'un concours d'identification de bio-marqueurs du TDAH, plusieurs instituts de neuro-imageries se sont rassemblés pour pre-process le ADHD200 et le résultat de cet effort collectif est [téléchargable](https://www.nitrc.org/frs/?group_id=383). 

Étapes:
1. Consulter l'article original portant sur la base de données + comprendre sa structure
2. Sélectionner l'initiative (quel sous-ensemble de données de la section ADHD200 Prepoc Athena) -> critères: accessible, stockable, utilisable
3. Documenter la structure des données (si nécessaire)
4. Répliquer le projet initial + documenter les changements nécessaires et les difficultés rencontrées

*Si cette tâche s'avère plus demandante que prévue (excède 10h de travail), je vais entraîner moins de modèles de classificateur que le projet initial.*


### Tâche 3: Ajouter une visualisation pertinente des résultats
Les visualisations exactes seront déterminées après la complétion de la tâche 2, mais voici quelques options que je considère:
- Réplication des graphiques originaux (mais avec la nouvelle base de données) + améliorations si possible (clareté, accessibilité)
- Différences des résultats entre la réplication du projet initial avec base de données Nilearn et la nouvelle base de données
- Évaluation de la performance (ajout de critères différents que projet original)

*Selon la charge de travail, la quantité de visualisation et la sélection dans les options présentées ci-dessus seront variables*

### En cas de surcharge de travail global:
Seulement les tâches 1 et 2 seront effectués (des visualisations avec une charge de travail insuffisante pour être considérée une tâche complète seront quand même incluse dans la tâche 2 afin de visualiser les résultats)
