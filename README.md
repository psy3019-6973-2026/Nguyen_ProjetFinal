# Projet final - PSY 3019

## Projet initial - [ADHD diagnosis prediction using machine learning de Iangola Andrianarison](https://school-brainhack.github.io/project/adhd-prediction/)
**Objectif du projet:**
Entrainer des modèles de classifications sur des données IRMf pour prédire des diagnostics de trouble du déficit de l'attention avec ou sans hyperactivité (TDAH)

Le projet initial est effectué avec une base de données accessible avec Nilearn, le Nitric ADHD resting-state. L'auteure a seulement utilisé un sous-ensemble de la base de données (30 participants, 13 ADHD, 17 contrôle) et celui-ci est déjà pré-processed.

Données phénotypiques: statut diagnostic, mesures de symptômes TDAH, âge, sexe, quotient intellectuel et status de médication

Plusieurs modèles de comparaisons ont étés effectués (KNN, Régression logistique, Arbre de décision, Random Forest, Machine à vecteurs de support (SVM) et XGBoost) et leur performance ont été évalué par F1 score, accuracy et matrices de confusions.


## Intérêt personnel
Je suis tout d'abord intéresser à apprendre à entraîner des modèles de classificateur, élément beaucoup mentionné durant mon parcours au baccalauréat mais dont je n'ai malheureusement pas eu la chance d'appliquer pratiquement. 

De plus, le TDAH est un sujet qui m'intéresse puisqu'il m'affecte personnellement et il semble également être un souci au niveau de la santé publique au Québec. 

[Faits saillants:](https://www.lapresse.ca/actualites/sante/telemedecine/60-minutes-pour-un-diagnostic-de-tdah/2024-11-20/il-risque-d-y-avoir-une-perte-de-precision-dans-le-diagnostic.php)
- Autour de 14 % des Québécois de 10 à 17 ans consommaient des psychostimulants spécifiques au TDAH en 2017. (ce qu'on devrait observer: 2-5 %)
- Prévalence du TDAH chez les Québécois de moins de 25 ans: 6,4 % VS 2,4 % chez les autres jeunes Canadiens.
- Une évaluation neuropsychologique requiert généralement de quatre à huit heures d’entretiens, en une ou plusieurs séances MAIS plusieurs ont eu leur diagnostic en une rencontre virtuelle de 60 minutes. --> risque de perte de précision dans le diagnostic

Dans un système de santé où il semble avoir un manque perpetuel de temps et de ressource, une méthode quantitative robuste et qui serait probablement plus rapide qu'une consultation en neuropsychologie serait intéressante pour complémenter l'application actuelle dans l'évaluation de TDAH. 

## Tâches initialement proposées
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

## Tâches réalisées
Étant donné que la tâche 1 m'a pris plus de temps que prévu (en plus de problème personnel), les tâches 2 et 3 proposées n'ont pas été faits. Par contre, j'ai fait une autre tâche 2 qui était plus simple, soit la modification de la pipeline d'apprentissage.

### Tâche 1: Reproduire le projet intial (notebook) à partir d’un environnement vierge et documenter le processus

#### Modifications mineures:
- Différences des valeurs de bases de certaines fonctions nilearn, donc j'ai dû apporter certaines modifications afin d'avoir les mêmes visualisations et analyses. Par exemple: valeur de cmap par défaut qui était différent, précision de quelle résolution qu'on veut pour l'atlas (vient aussi avec un changement des keys)
- Ajout d'un fichier environement yml: étant donné qu'on a déjà utilisé le dataset en classe, j'ai réutilisé l'environnement du cours de visualisation, mais j'ai ajouté xgboost puisqu'il était un classificateur utilisé dans le projet
- Changer les paths pour l'enregistrement des données et figures: au lieu de le hardcode comme le projet original, j'ai mis des paths relatifs (donc non spécifique à l'ordinateur local) et pour l'enregistrement des figures j'ai utilisé le module os pour créer des fichiers

#### Modifications / problèmes majeurs:

**Problème avec la fonction datasets.fetch_adhd de nilearn**

Malgré que je précise le nombre de sujets (40), j'arrive à bien download toutes les données phénotypes mais lorsque j'appelle avec la fonction nilearn data.phenotypic on me retourne les données phénotypes que pour 30 participants (ce n'est d'ailleurs pas les mêmes 30 participants que le projet original, une différence observable lorsqu'on regarde les distributions de diagnostics de TDAH et d'âge).

<img width="561" height="456" alt="Capture d’écran, le 2026-04-23 à 02 44 21" src="https://github.com/user-attachments/assets/88de212f-a0e8-4347-be20-ae492a871181" /><img width="561" height="419" alt="Capture d’écran, le 2026-04-23 à 02 44 43" src="https://github.com/user-attachments/assets/be7c5a52-a977-482d-80eb-e0ff4c573fca" />

<img width="848" height="348" alt="Capture d’écran, le 2026-04-23 à 02 45 56" src="https://github.com/user-attachments/assets/460e44be-3aaa-4d4a-90cf-db609984ba4e" />
<img width="848" height="348" alt="Capture d’écran, le 2026-04-23 à 02 45 42" src="https://github.com/user-attachments/assets/70c34ab4-e122-4c51-8a13-f964789cfb04" />

Pour résoudre le problème, je suis allé manuellement chercher les données phénotypes puisque le download avait bien fonctionné. Par contre, ce problème est quand même important à résoudre pour nilearn, donc j'ai posté un [issue sur leur repo](https://github.com/nilearn/nilearn/issues/6190). J'ai réussi à identifier quel endroit semblait être problématique, mais je n'ai pas trouvé de solution. 

**Problème avec l'initialisation du ConnectivityMeasure**

Voici le code original: 
<img width="613" height="304" alt="Capture d’écran, le 2026-04-23 à 02 56 38" src="https://github.com/user-attachments/assets/d213f1c1-3c10-48e5-87a9-f4d0ae405684" />
Le problème est qu'il initialise une mesure de connectivité avec certains critères et ensuite à chaque itération de la boucle, il change les critères de la mesure de connectivité et n'utilise juste pas celle précédemment initialisée.

Personnellement, je préfères la version avec discard_diagonal=True et vectorize=True étant donné qu'on n'a pas besoin de flatten les données (déjà de shape 1D) et ça permet aussi d'avoir moins de redondance dans les informations qu'on donne aux classificateurs.

Puisque l'objectif de la tâche 1 était de reproduire le notebook original, j'ai utilisé la version dans la boucle puisque c'est celle qui a été utilisé sur ses données, mais ma préférence pour l'autre a mené à la tâche 2 afin de pouvoir comparer si les paramètres de ConnectivityMeasure vont avoir un impact sur la performance des classificateurs (additionnellement, une comparaison entre la méthode d'entraînement précédemment utilisée sera aussi comparée avec une méthode de validation croisée à la tâche 2)

#### Comparaisons des résultats

**Modèle original (30 sujets)**
<img width="1500" height="1000" alt="confusion_matrices" src="https://github.com/user-attachments/assets/51308e43-655a-4cc6-80fc-32681be1b836" />

**Modèle 1 (40 sujets et ConnectivityMeasure original)**
<img width="1500" height="1000" alt="Modele1" src="https://github.com/user-attachments/assets/3e876a66-7631-41e8-b00e-e9de42c2730b" />


**Modèle original**
<img width="1000" height="600" alt="classifier_performance_comparison" src="https://github.com/user-attachments/assets/943312c2-31c6-4621-86c8-4cf349483b24" />

**Modèle 1**
<img width="1000" height="600" alt="Modele1" src="https://github.com/user-attachments/assets/044699e3-6b01-4ec2-81c6-69e8cd12cea2" />


Pour le modèle 1, le meilleur classificateur en terme d'accuracy est le KNN (0.75) et le meilleur en terme du F1 score est le SVM (0.73). Tous les autres classificateurs ont une performance moins ou égale à de la chance.

Entre le modèle original et le modèle 1, il y a une baisse notable de la performance du logistic regression, du decision Tree et du Random Forest. Par contre, le modèle montre une augmentation dans les deux scores de performance du KNN et du XGBoost ainsi que dans le F1 score du SVM.

En comparant les matrices de confusions entre les modèles, il semble que globalement les classificateurs du modèle 1 a un peu moins de biais à presque systématiquement prédire que le sujet a un TDAH.

Cependant, il faut se rappeler que, globalement, les classificateurs restent quand même assez mauvais. 


### Tâche 2: Modification du pipeline d'apprentissage

Comme expliquée plus tôt, j'ai voulu testé l'effet d'avoir moins de redondance dans les données qu'on donnait aux classificateurs soit d'enlever la diagonale et le triangle inférieur de la matrice de corréalation ce qui donne au final moins de features mais aucun doublons. Donc pour le modèle 2, la seule modification que j'ai apporté est que la mesure de connectivité = ConnectivityMeasure(kind='correlation', vectorize=True, discard_diagonal=True, standardize='zscore_sample'). 

Ensuite, étant donné qu'un échantillon de 40 sujets reste tout de même petit, je me suis demandé si nos précédents résultats sont biaisés par comment ceux-ci sont diviser. J'ai ainsi ajouter dans le pipeline d'apprentissage une validation croisée pour le modèle 3 (pour ce modèle j'ai également conservé le mesure de connectivité du modèle 2)

Variables pour la validation croisée:
- cross_val = StratifiedKFold(n_splits=5, shuffle=True, random_state=123)
- y_pred = cross_val_predict(clf, X, y, cv=cross_val)

#### Résultats

**Modèle 2 (40 sujets et nouvelle ConnectivityMeasure)**
<img width="1500" height="1000" alt="Modele2" src="https://github.com/user-attachments/assets/6af03e0e-c35b-4699-a814-4f369c66ef3e" />


<img width="1000" height="600" alt="Modele2" src="https://github.com/user-attachments/assets/b4e8fede-de61-4326-81cd-e970e6792fb2" />


**Modèle 3 (40 sujets, nouvelle ConnectivityMeasure et validation croisée)**

<img width="1500" height="1000" alt="Modele3" src="https://github.com/user-attachments/assets/3b7e2144-a099-491b-8377-65c8173f736f" />


<img width="1000" height="600" alt="Modele3" src="https://github.com/user-attachments/assets/f942a60f-a7d9-49a9-b66a-6f89ce663cad" />




#### Tableau résumé des classificateurs de tous les modèles 

| Classificateurs | Accuracy M1 | F1 M1 | Accuracy M2 | F1 M2 | Accuracy M3 | F1 M3 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| KNN | 0.750 | 0.667 | 0.750 | 0.667 | 0.425 | 0.303 |
| Logistic Regression | 0.250 | 0.250 | 0.250 | 0.250 | 0.375 | 0.419 |
| Decision Tree | 0.375 | 0.444 | 0.375 | 0.444 | 0.650 | 0.667 |
| Random Forest | 0.500 | 0.500 | 0.250 | 0.400 | 0.475 | 0.432 |
| SVM | 0.625 | 0.727 | 0.625 | 0.723 | 0.350 | 0.435 |
| XGBoost | 0.500 | 0.500 | 0.375 | 0.444 | 0.475 | 0.488 |


*M1 : Réplication projet original — M2 : Sans redondance des features — 
M3 : Sans redondance des features avec validation croisée*


Pour le modèle 2, toutes les performances sont identiques au modèle 1 sauf pour le XGBoost et le RandomForest (diminution d'accuracy et au F1 score). Il semble donc que retirer la redondance des features n'a pas eu beaucoup d'impact sur les performances des classificateurs. 

Pour le modèle 3, on voit une diminution globale sur les performances à l'execption du Decision Tree et du Logistic Regression qui ont une augmentation. En effet, quand on retire la redondance des features et qu'on ajoute une validation croisée, aucun des classificateurs ont des performances en haut de la chance, mise à part le Decision Tree. Je ne pense pas que cela signifie que cette méthode n'est pas la bonne. Je pense plutôt qu'on a eu de la chance avec le spit des données des modèles 1 et que les performances au modèle représenteraient des scores moins "gonflés" et qui réflètent mieux la capacité de généralisation des classificateurs. 

## Déclaration de l'usage de l'IA
Ce projet a été assité par l'IA pour: 
- debug lorsque cela me prenait trop de temps par moi-même/en lisant la documentation nilearn (ex. trouver qu'elle cmpa étati utilisé dans les figures originales)
- aider la compréhension









