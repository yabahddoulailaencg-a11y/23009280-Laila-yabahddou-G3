# Examen individuel : Projet de science des données appliqué à la finance

**S7, ENCG-2026** · Épreuve pratique individuelle de 2 heures

Chaque étudiant traite seul, en **deux heures**, le sujet qui lui a déjà été attribué : il mène un projet complet de science des données avec un algorithme choisi parmi les 29 du support de cours, puis le défend en soutenance individuelle. **Le travail final et complet doit être soumis sur le lien https://forms.gle/SmfW9kbcNbsz4Q8a7**

## Informations générales

| Élément | Précision |
| --- | --- |
| Public | Étudiants de S7, filières FIN et CI |
| Cours | BD & DS|
| Modalité | Épreuve pratique individuelle notée, sur machine |
| Durée | 2 heures, en séance |
| Sujet | Celui qui vous a déjà été attribué |
| Langage | Python 3.10 ou plus récent (pandas, NumPy, matplotlib, scikit-learn) |
| Dépôt GitHub | Public, nommé `CodeApogee-Nom-Groupe` (section 9) |
| Soutenance | 8 minutes par étudiant, lors de la séance suivante |
| Pondération | 30 % de la note du cours |
| Documents fournis | Support `Tp_ML.ipynb` (29 algorithmes) et liste `projets_finance_science_donnees.md` (fiches des sujets) |

### À faire avant la séance (obligatoire)

- Créer un dépôt GitHub **public** nommé `CodeApogee-Nom-Groupe` (règles de nommage en section 9), avec ses dossiers, un README à compléter et un `.gitignore`, puis communiquer son lien à l'enseignant.
- Télécharger les données de votre sujet, les enregistrer dans `data/raw/` du dépôt et noter la date d'extraction.
- Placer la fiche de votre sujet dans `docs/`.
- Vérifier que l'environnement fonctionne : les imports du support s'exécutent sans erreur.
- **Aucun code d'analyse n'est écrit avant la séance.** L'historique des commits en fait foi.

### Déroulé minuté de la séance

| Horaire | Étape | Ce qui doit exister à la fin de l'étape |
| --- | --- | --- |
| 0:00 à 0:10 | Sujet et problématique (section 3) | En-tête du notebook rempli (annexe B) |
| 0:10 à 0:25 | Jeu de données (section 4) | Chargement vérifié, description et dictionnaire des variables ; premier commit |
| 0:25 à 0:50 | Exploration et préparation (section 5) | Trois graphiques interprétés, pipeline de préparation |
| 0:50 à 1:25 | Apprentissage et évaluation (section 6) | Référence, modèle réglé, résultats sur le test, analyse des erreurs ; deuxième commit |
| 1:25 à 1:40 | Compte rendu (section 7) | Analyse critique et conclusion rédigées, notebook exporté en PDF |
| 1:40 à 1:52 | Présentation (section 8) | Six diapositives en PDF |
| 1:52 à 2:00 | Dépôt final (section 9) | README complété, dépendances, commit final étiqueté `remise-finale` |

## 1. Contexte et objectifs pédagogiques

Ce TP vous demande d'appliquer **un** des 29 algorithmes du support au sujet de finance qui vous a été attribué, sur des données publiques, en menant seul toute la démarche en deux heures. Le support `Tp_ML.ipynb` a présenté ces algorithmes sur des jeux d'exemple (Diabetes, Breast Cancer, Wine, Digits, Taxi). Il s'agit maintenant d'aller de la question posée jusqu'à une conclusion argumentée.

Le travail est évalué comme un examen pratique. La performance brute du modèle compte peu : ce sont vos choix, leur justification et votre capacité à les expliquer qui sont notés. Un modèle qui ne bat pas sa référence, honnêtement évalué et bien analysé, peut obtenir une très bonne note.

Dans le temps imparti, un travail simple, correct et bien expliqué vaut mieux qu'un travail ambitieux et inachevé. Respectez le déroulé minuté ci-dessus.

À la fin du TP, vous saurez :

1. Formuler une problématique précise et un objectif mesurable à partir d'un besoin financier.
2. Sélectionner, documenter et critiquer un jeu de données public.
3. Explorer et préparer des données sans fuite d'information, y compris sur des séries temporelles.
4. Choisir, expliquer et régler un algorithme adapté au problème.
5. Évaluer un modèle avec un protocole rigoureux et le comparer à une référence simple.
6. Interpréter les résultats, leurs erreurs et leurs limites.
7. Communiquer un projet par écrit (compte rendu intégré au notebook), à l'oral (six diapositives) et sous une forme reproductible (dépôt GitHub).

## 2. Prérequis et modalités de travail individuel

### Prérequis

- Python : pandas, NumPy, matplotlib et scikit-learn, au niveau du support.
- Les questions communes Q1 à Q4 du support (présentation, schéma, contextes d'utilisation, analyse expérimentale) : elles servent de base à la partie « algorithme » de votre compte rendu.
- Statistique descriptive : moyenne, écart-type, corrélation, intervalle de confiance.
- Git et GitHub : créer un dépôt, faire des commits, rédiger un README. Un compte GitHub personnel est nécessaire.

### Environnement

- Google Colab ou Jupyter en local.
- Bibliothèques du support : scikit-learn, xgboost, umap-learn, gymnasium.
- D'autres bibliothèques sont autorisées si elles figurent dans le fichier de dépendances et sont déclarées dans le compte rendu, par exemple statsmodels pour les tests de significativité ou shap pour F27.

### Règles du travail individuel

- Chaque étudiant travaille seul, sur son sujet, son notebook, sa présentation et son dépôt.
- Toute communication avec un autre étudiant est interdite pendant la séance, de même que le partage de code, de résultats ou de fichiers.
- Documents autorisés : le support du cours, vos notes, la documentation officielle des bibliothèques. Les outils d'IA suivent les règles de la section 11.
- Faites des commits réguliers (au moins trois pendant la séance) : un problème de connexion en fin d'épreuve ne justifie pas un retard.
- En cas de problème technique bloquant, prévenez immédiatement le surveillant ; l'incident est noté avec l'heure.

## 3. Étape 1 : sujet attribué et problématique (0:00 à 0:10)

### 3.1 Votre sujet et les algorithmes compatibles

Votre sujet vous a déjà été attribué. Sa fiche détaillée (question, données, prétraitement, modèles, métriques, risques) se trouve dans `projets_finance_science_donnees.md`. Le tableau indique, pour chaque sujet, les algorithmes du support qui conviennent (numéros de l'annexe A). Si votre sujet n'y figure pas, choisissez un algorithme du support adapté à sa tâche et justifiez ce choix.

Quand une fiche cite plusieurs modèles, vous en retenez **un seul comme algorithme principal**, parmi les 29 du support. Les autres peuvent servir de comparaison facultative. Une méthode absente du support (LOF, GARCH, Holt-Winters, analyse factorielle) ne peut pas être votre algorithme principal.

| N° | Sujet | Type de tâche | Algorithmes compatibles | Point d'attention |
| --- | --- | --- | --- | --- |
| F1 | Risque de crédit en Allemagne | Classification binaire à coûts asymétriques | 8 à 16 | Le seuil de décision fait partie du livrable. |
| F2 | Prévision du taux à 10 ans | Régression sur série temporelle | 1, 2, 3, 5, 6, 7, 16 | Les modèles à arbres n'extrapolent pas au-delà des valeurs vues à l'apprentissage. |
| F3 | Prévision de l'inflation | Régression sur séries mensuelles | 1, 2, 3, 6, 7, 16 | Séries révisées après publication (biais d'anticipation). |
| F4 | Sentiment des nouvelles financières | Classification de texte à trois classes | 8, 10, 12, 13, 14 | Pour Naive Bayes, utiliser la variante multinomiale, adaptée au texte ; le support montre la variante gaussienne. |
| F5 | Facteurs de risque d'un portefeuille | Régression linéaire multiple | 1 (2 en comparaison) | Rendements du portefeuille à collecter vous-même ; tests avec statsmodels autorisés. |
| F6 | Récessions et courbe des taux | Classification déséquilibrée | 8, 11, 12, 14, 15, 16 | Une dizaine de récessions seulement : préférer un modèle simple. |
| F7 | Anomalies sur le S&P 500 | Détection d'anomalies | 24 (19 ou 20 possibles) | LOF n'est pas dans le support : comparaison facultative seulement. |
| F8 | Battre la marche aléatoire | Classification binaire | 8 à 16 | Déclarer tous les modèles et réglages essayés (*data snooping*). |
| F9 | Régimes de marché | Partitionnement | 17, 18, 19, 20 | Standardiser avec une fenêtre passée uniquement. |
| F10 | Gestion de position par renforcement | Apprentissage par renforcement | 27, 28 | Le DQN (29) n'est traité que de façon conceptuelle dans le support : à ne pas implémenter dans le temps imparti. |
| F11 | Volatilité euro-dollar | Régression sur série temporelle | 1, 2, 3, 6, 7, 16 | GARCH hors support : comparaison facultative. |
| F12 | Prix du pétrole WTI | Régression sur série temporelle | 1, 2, 3, 6, 7, 16 | Prix négatif du 20 avril 2020 à traiter et à signaler. |
| F13 | Pics de volatilité (VIX) | Classification déséquilibrée | 8, 11, 12, 14, 15, 16 | Fenêtres chevauchantes : pas de validation croisée aléatoire. |
| F14 | Taux hypothécaire et taux à 10 ans | Régression linéaire | 1, 2, 3 | Données hebdomadaires et quotidiennes à aligner. |
| F15 | Moral des ménages et croissance | Régression sur séries trimestrielles | 1, 2, 3, 7 | Peu d'observations : limiter la complexité du modèle. |
| F16 | Loi d'Okun | Régression linéaire simple | 1 | Un seul prédicteur : travail centré sur l'inférence et la stabilité du coefficient. |
| F17 | Mises en chantier de logements | Régression avec saisonnalité | 1, 2, 3, 6, 7, 16 | Holt-Winters hors support : comparaison facultative. |
| F18 | Rendements hebdomadaires du Dow Jones | Régression ou classification | 1, 2, 3, 6, 7 ou 8, 11, 12, 14 | Une seule année de données. |
| F19 | Groupes de titres du Dow Jones | Partitionnement | 17, 18, 20 | 30 titres seulement : DBSCAN est peu adapté à un si petit effectif. |
| F20 | Courbe des taux par ACP | Réduction de dimension | 21 | Analyse factorielle hors support : comparaison facultative. |
| F21 | Force du dollar | Régression sur série temporelle | 1, 2, 3, 6, 7, 16 | Période courte (depuis 2006). |
| F22 | Anticipations d'inflation | Régression sur séries mensuelles | 1, 2, 3 | Le taux implicite contient une prime de risque. |
| F23 | Spread de crédit Baa et récessions | Classification déséquilibrée | 8, 11, 12, 14, 15, 16 | Recoupe F6 : comparer au pouvoir prédictif de l'écart 10 ans moins 2 ans. |
| F24 | Corrélation Nasdaq et S&P 500 | Régression sur une mesure glissante | 1, 2, 3, 6, 7, 16 | Les deux séries ne se recouvrent que depuis 2016 environ. |
| F25 | Taux directeur et pente de la courbe | Régression linéaire | 1, 2 | Une corrélation ne prouve pas l'effet de la politique monétaire. |
| F26 | Scoring de crédit australien | Classification binaire | 8 à 16 | Même base de demandes que F27 sous une autre forme. |
| F27 | Scoring de crédit explicable | Classification et explicabilité | 14 ou 16 en principal, 8 obligatoire en comparaison | SHAP hors support, autorisé comme outil d'explication. |
| F28 | Portefeuilles taille et valeur | Régression multiple sur 25 portefeuilles | 1 | Test conjoint des alphas nuls à programmer ou à faire avec statsmodels. |
| F29 | Prévisibilité du momentum | Classification binaire | 8, 11, 12, 14, 16 | Krachs du momentum rares et massifs : examiner les pertes extrêmes. |
| F30 | Value-at-Risk | Estimation et backtesting | 7, en régression avec perte quantile | VaR historique et paramétrique comme références ; GARCH hors support. |

- La série FRED SP500 ne couvre qu'environ les dix dernières années (F7 à F10, F24) : vos conclusions doivent en tenir compte.
- Les algorithmes 22 (t-SNE), 23 (UMAP), 25 (bandits manchots), 26 (epsilon-greedy) et 29 (DQN) ne correspondent directement à aucun sujet : ne les retenez pas comme algorithme principal. L'ACP, t-SNE et UMAP peuvent en revanche servir de visualisation complémentaire.
- La variante régression ou classification d'un algorithme du support est acceptée (par exemple KNN ou XGBoost en régression, alors que le support les montre en classification), à condition d'expliquer la différence.

### 3.2 Présenter le sujet et formuler la problématique

À rédiger dans l'en-tête du notebook (modèle en annexe B), pendant les dix premières minutes :

1. **Intérêt du sujet.** Votre intérêt pour le sujet, la pertinence du problème et l'utilité des résultats : qui utiliserait ce résultat, et pour quelle décision ?
2. **Problématique.** Une question précise à laquelle vos données peuvent répondre. Évitez les questions trop larges, du type « Peut-on prédire la bourse ? ».
3. **Objectif mesurable.** Une métrique principale, une référence simple, une période ou un jeu de test, et un seuil de réussite fixé **avant** de voir les résultats de test. Exemple de forme, sur un sujet hors liste : « Prévoir le nombre mensuel de sinistres d'un assureur avec une MAE inférieure d'au moins 10 % à celle de la moyenne saisonnière, sur les 24 derniers mois. »
4. **Nature du problème.** Régression, classification (binaire, multiclasse, déséquilibrée), partitionnement, détection d'anomalies, réduction de dimension ou apprentissage par renforcement. Justifiez ce choix par la forme de la variable à prédire, ou par l'absence de variable cible.

## 4. Étape 2 : description du jeu de données (0:10 à 0:25)

Présentez le jeu de données dans la section 2 du notebook, avant toute analyse. Les éléments suivants sont obligatoires :

- **Nom, source exacte et lien d'accès** (URL complète), avec la **date d'extraction**. Les séries FRED sont mises à jour en continu : la date permet de reproduire vos chiffres.
- **Conditions d'utilisation ou licence**, lorsque la source les indique. Si rien n'est indiqué, écrivez-le.
- **Taille** : nombre d'observations et de variables, période couverte, fréquence (quotidienne, mensuelle, etc.).
- **Unité d'observation** : ce que représente une ligne (un jour de bourse, un dossier de crédit, un mois, un titre).
- **Dictionnaire des principales variables (cinq à huit suffisent)**, sur le modèle ci-dessous.
- **Variable cible**, si elle existe, et la façon dont vous la construisez.
- **Adéquation** : pourquoi ce jeu permet de répondre à votre problématique.
- **Limites** : valeurs manquantes, déséquilibre des classes, biais de sélection ou de survie, représentativité, ancienneté, révisions des séries, changements de régime.

Modèle de dictionnaire :

| Variable | Description | Type | Unité | Rôle | Manquants (%) |
| --- | --- | --- | --- | --- | --- |
| *nom dans le fichier* | *ce qu'elle mesure* | *numérique, catégorielle, date, texte* | *%, $, points d'indice* | *cible, explicative, date, identifiant* |  |

Une variable que vous créez (retard, moyenne glissante, écart entre deux taux) figure aussi dans le dictionnaire, avec sa formule.

## 5. Étape 3 : exploration et préparation des données (0:25 à 0:50)

### 5.1 Structure attendue du notebook

Le notebook est à la fois votre code et votre compte rendu : ses titres suivent les dix sections du plan imposé (section 7 et annexe B).

1. **En-tête et section 1** : modèle de l'annexe B (sujet, problématique, objectif mesurable), versions de Python et des bibliothèques.
2. **Configuration** : imports, graine aléatoire (`GRAINE = 42`, comme dans le support), chemins relatifs.
3. **Section 2, jeu de données** : chargement et vérification (dimensions, types, premières lignes, plage de dates et fréquence), puis description du jeu selon la section 4 de cet énoncé.
4. **Section 3, exploration** : statistiques descriptives utiles au problème ; qualité des données (valeurs manquantes, doublons, valeurs atypiques), avec pour chaque problème la méthode de détection, la décision prise et sa justification. En finance, une valeur extrême est souvent réelle (krach, crise) : ne la supprimez pas sans raison. Au moins trois graphiques adaptés, avec un titre, des axes nommés et des unités.
5. **Section 4, préparation** : nettoyage, création de variables, encodage, mise à l'échelle et découpage, chacun justifié. La mise à l'échelle dépend de l'algorithme retenu : expliquez pourquoi elle est nécessaire ou non.
6. **Sections 5 à 7, algorithme, protocole et résultats** : selon la section 6 de cet énoncé.
7. **Sections 8 à 10, analyse critique, conclusion et références** : selon la section 7.
8. **Déclaration des ressources et outils d'IA** : selon la section 11.

**Règle d'interprétation.** Chaque résultat ou graphique important est suivi d'une cellule de texte de deux à quatre lignes : ce qu'il montre, et ce que vous en concluez. Une sortie sans commentaire ne rapporte aucun point.

### 5.2 Règles contre les fuites de données (obligatoires)

Une fuite de données se produit quand le modèle utilise, pendant l'apprentissage, une information qui ne serait pas disponible au moment de la prédiction. Les résultats paraissent alors meilleurs qu'ils ne le sont. Chaque règle non respectée coûte des points au critère 4 du barème.

1. **Découper avant de transformer.** Toute transformation qui apprend quelque chose des données (imputation, standardisation, encodage, sélection de variables, ACP, rééquilibrage des classes) s'ajuste sur l'apprentissage seulement (`fit`), puis s'applique à la validation et au test (`transform`).
2. **Utiliser un `Pipeline`**, avec `ColumnTransformer` si les variables sont de types différents, pour que ces transformations soient réajustées dans chaque pli de validation croisée.
3. **Respecter l'ordre du temps.** Pour des données datées, le test est postérieur à l'apprentissage, sans mélange aléatoire (`shuffle=False`). La validation croisée se fait avec `TimeSeriesSplit` ou par fenêtre glissante.
4. **Construire les variables avec le passé seulement.** Un retard utilise `shift(k)` avec k positif ; une moyenne glissante se termine à la date t ; la cible est décalée vers le futur, puis les lignes incomplètes sont retirées. Affichez quelques lignes (date, variables, cible) pour prouver l'alignement.
5. **Laisser un écart quand la cible porte sur un horizon.** Si la cible couvre h périodes (récession dans les 12 mois, pic du VIX dans les 5 jours), laissez au moins h observations entre la fin de l'apprentissage et le début du test.
6. **Ne jamais standardiser une série temporelle avec toute la série**, y compris en non supervisé : utilisez les statistiques de l'apprentissage ou d'une fenêtre passée.
7. **Exclure les variables qui contiennent la cible**, même indirectement : par exemple l'indicateur de récession du mois courant, ou un prix de la semaine à prévoir.
8. **N'utiliser le jeu de test qu'une seule fois**, à la fin. Les hyperparamètres se règlent en validation. Indiquez le nombre de configurations essayées.
9. **Signaler les révisions de données.** Si vous utilisez la version actuelle d'une série révisée (inflation, PIB, mises en chantier), écrivez-le comme une limite. Pour aller plus loin, l'archive ALFRED de la Réserve fédérale de Saint-Louis conserve les versions publiées à chaque date.

## 6. Étape 4 : apprentissage, évaluation et interprétation (0:50 à 1:25)

### 6.1 Choisir et présenter l'algorithme

- Retenez **un algorithme principal** parmi les 29 de l'annexe A.
- Justifiez son adéquation : nature de la tâche, taille des données, types de variables, relations attendues (linéaires ou non), besoin d'interprétation, déséquilibre des classes. Expliquez aussi pourquoi vous n'avez pas retenu au moins un autre algorithme plausible.
- Présentez son principe en 6 à 10 lignes, en vous appuyant sur la question Q1 du support : intuition, étapes d'apprentissage, formule essentielle avec **tous ses symboles définis**, distinction entre paramètres appris et hyperparamètres.
- Décrivez au moins deux hyperparamètres importants et leur effet attendu.
- Un second modèle de comparaison est facultatif. Il n'est valorisé que s'il est analysé, et non simplement affiché.

### 6.2 Définir le protocole d'évaluation

**Référence simple obligatoire.** Votre modèle est toujours comparé à une règle naïve, sans apprentissage ou presque. Quand la fiche du sujet propose un modèle de référence (par exemple une régression logistique), il peut s'ajouter à la règle naïve, mais il ne la remplace pas.

| Type de tâche | Exemples de référence naïve |
| --- | --- |
| Régression sur série temporelle | Dernière valeur observée (marche aléatoire), moyenne historique, moyenne saisonnière |
| Régression sans dimension temporelle | Moyenne ou médiane de la cible sur l'apprentissage |
| Classification | Classe majoritaire, tirage selon les fréquences des classes, règle de seuil sur une seule variable |
| Partitionnement | Règle de seuil sur une variable, par exemple volatilité au-dessus ou au-dessous de sa médiane passée |
| Détection d'anomalies | Observation située à plus de trois écarts-types de la moyenne |
| Réduction de dimension | Une seule composante |
| Apprentissage par renforcement | Position fixe (achat et conservation), position neutre, politique aléatoire |

**Découpage.** Sans dimension temporelle : apprentissage, validation (ou validation croisée) et test, avec stratification pour une classification déséquilibrée. Avec des données datées : découpage chronologique, avec les dates de début et de fin de chaque période écrites dans le compte rendu.

**Réglage des hyperparamètres.** Validation croisée (`KFold`, `StratifiedKFold` ou `TimeSeriesSplit`) avec `GridSearchCV` ou `RandomizedSearchCV`, sur l'apprentissage seulement. Dans le temps imparti, limitez-vous à un ou deux hyperparamètres, sur trois à cinq valeurs chacun. Fixez toutes les graines aléatoires.

**Métriques.** Choisissez une métrique principale avant de voir les résultats, puis une ou deux métriques secondaires. Pour chacune, expliquez ce qu'elle mesure, son unité et pourquoi elle convient à votre problème, en tenant compte d'un éventuel déséquilibre des classes ou de valeurs extrêmes.

**Incertitude.** Donnez la moyenne et l'écart-type des scores sur les plis de validation, ou un intervalle obtenu par rééchantillonnage.

### 6.3 Présenter et interpréter les résultats

1. Un **tableau comparatif** : référence et modèle, en validation et en test, avec la métrique principale et les secondaires.
2. Une **courbe de validation** (score selon un hyperparamètre) ou une courbe d'apprentissage, pour discuter le surapprentissage en comparant les scores d'apprentissage et de test.
3. Une **analyse des erreurs** : où et quand le modèle se trompe-t-il (périodes, classes, montants) ? Matrice de confusion, résidus dans le temps ou cas les plus mal prédits.
4. Une **interprétation prudente des variables** (coefficients, importance par permutation), sans confondre corrélation et causalité.
5. La **capacité de généralisation** : écart entre apprentissage et test, stabilité sur deux sous-périodes ou plusieurs graines.
6. Une **illustration d'usage** sur 3 à 5 observations non utilisées pour l'apprentissage : entrée, prédiction, valeur réelle et commentaire.
7. Une **réponse explicite à la problématique** : l'objectif mesurable est-il atteint ? Un résultat négatif honnête et expliqué vaut mieux qu'un bon score mal établi.

### 6.4 Adapter les consignes à la famille de l'algorithme

Les consignes 6.2 et 6.3 sont écrites pour l'apprentissage supervisé (algorithmes 1 à 16). Pour les autres familles, ne forcez pas un protocole de classification : appliquez le tableau suivant.

| Famille | Ce qui remplace la prédiction d'une cible | Évaluation attendue | Usage sur des données non vues | Piège à éviter |
| --- | --- | --- | --- | --- |
| Partitionnement (17 à 20) | Description des groupes : profil moyen, taille, périodes couvertes | Choix du nombre de groupes (coude, silhouette, BIC pour les mélanges gaussiens) ; stabilité selon la graine et la sous-période ; comparaison a posteriori avec une variable externe (USREC, secteur), jamais utilisée pour l'apprentissage | Affecter de nouvelles observations à un groupe. K-means et mélanges gaussiens ont une méthode `predict` ; la CAH et DBSCAN n'en ont pas : justifiez votre règle d'affectation | Des groupes qui reflètent la période ou l'échelle des variables plutôt qu'une structure réelle |
| Réduction de dimension (21 à 23) | Interprétation des axes : variance expliquée, contributions des variables | Part de variance expliquée, erreur de reconstruction (ACP), comparaison avec une seule composante | Projeter de nouvelles observations (`transform` pour l'ACP et UMAP ; t-SNE ne le permet pas) | Interpréter les distances entre groupes éloignés d'une carte t-SNE |
| Détection d'anomalies (24) | Liste datée des observations atypiques, avec leur score | Proportion détectée, sensibilité au paramètre `contamination`, confrontation à des événements documentés et sourcés, comparaison avec la règle des trois écarts-types | Ajuster le modèle sur le passé, puis noter une période postérieure | Confondre atypique et erroné |
| Renforcement (25 à 29) | Politique apprise : action choisie dans chaque état | Apprentissage sur une période, test sur une période postérieure avec la politique figée (sans exploration) ; au moins 3 graines ; rendement cumulé, ratio de Sharpe, perte maximale (*drawdown*), nombre de changements de position, coûts compris | Rejouer la politique figée sur la période de test, jour par jour | Surapprendre le passé ; oublier les coûts de transaction |

En renforcement, documentez aussi l'environnement : états, actions, récompense, coûts et hypothèses simplificatrices. Si vous choisissez SARSA, la mise à jour doit utiliser l'action suivante réellement choisie par la politique : montrez-le dans votre code.

## 7. Étape 5 : compte rendu (rédigé au fil de l'épreuve, finalisé de 1:25 à 1:40)

**Le compte rendu est intégré au notebook.** Ses titres suivent le plan imposé ci-dessous et chaque section contient du texte rédigé : vos décisions, leur justification et l'interprétation des résultats. Un notebook réduit à une suite de cellules de code et de sorties brutes ne constitue pas un compte rendu. Rédigez chaque section au moment où vous la traitez, et gardez le dernier quart d'heure de cette étape pour l'analyse critique, la conclusion et l'export.

**Export.** Exportez le notebook exécuté en PDF dans `rapport/rapport.pdf` : dans Colab, menu Fichier puis Imprimer ; dans Jupyter, export en HTML puis impression en PDF depuis le navigateur.

**Plan imposé.**

| Section | Contenu attendu | Volume indicatif |
| --- | --- | --- |
| 1. Sujet et problématique | Intérêt du sujet, question, objectif mesurable, nature du problème | 5 à 8 lignes |
| 2. Jeu de données | Source, licence, taille, unité d'observation, dictionnaire, cible, limites, adéquation | 10 à 15 lignes et un tableau |
| 3. Exploration | Statistiques, trois graphiques interprétés, qualité des données | Une interprétation par graphique |
| 4. Préparation | Traitements, variables créées, prévention des fuites | 5 à 10 lignes |
| 5. Algorithme | Principe, formule, hyperparamètres, raisons du choix | 6 à 10 lignes |
| 6. Protocole expérimental | Découpage, référence, validation, métriques | 5 à 8 lignes |
| 7. Résultats | Tableau comparatif, graphiques, interprétation, analyse des erreurs | 10 à 15 lignes |
| 8. Analyse critique | Limites, biais, pistes d'amélioration concrètes | 5 à 8 lignes |
| 9. Conclusion | Réponse directe à la problématique et à l'objectif mesurable | 3 à 5 lignes |
| 10. Références et reproduction | Sources, lien du dépôt, instructions pour reproduire les résultats | Liste |

## 8. Étape 6 : présentation de six diapositives (1:40 à 1:52)

La présentation compte **exactement six diapositives**, sans diapositive de titre séparée, de remerciements ni d'annexe. Votre nom, votre code Apogée, votre groupe et le titre du sujet figurent sur la diapositive 1. Préparée en fin d'épreuve à partir des graphiques déjà enregistrés dans `figures/`, elle est remise au format PDF et présentée en **3 minutes** lors de la soutenance.

| N° | Titre imposé | Contenu attendu |
| --- | --- | --- |
| 1 | Sujet, problématique et objectifs | Question, objectif mesurable, intérêt du sujet |
| 2 | Dataset : source, variables et qualité des données | Source et période, unité d'observation, variables clés, problèmes de qualité |
| 3 | Exploration : principaux constats et graphiques | Un ou deux graphiques, chacun avec sa conclusion écrite |
| 4 | Préparation, algorithme et protocole d'évaluation | Traitements clés, algorithme et raison du choix, découpage, référence, métrique |
| 5 | Résultats, métriques et interprétation | Tableau modèle contre référence, un graphique de résultat, ce qu'il faut en retenir |
| 6 | Conclusion, limites et perspectives | Réponse à la problématique, deux ou trois limites, une piste d'amélioration |

Peu de texte, des graphiques lisibles avec leurs unités, et les mêmes chiffres que dans le notebook.

## 9. Étape 7 : dépôt GitHub et reproductibilité (1:52 à 2:00)

Chaque étudiant de S7 crée, avant la séance, un dépôt GitHub **public** qui rassemble **toutes les ressources nécessaires** à son projet. Le dépôt doit se suffire à lui-même : une personne qui le clone doit pouvoir tout réexécuter sans aucun autre fichier.

### Nom du dépôt

Le dépôt est nommé **`CodeApogee-Nom-Groupe`** :

- **Code Apogée** : votre numéro d'étudiant ;
- **Nom** : votre nom de famille, sans espace ni accent (par exemple « El Amrani » devient `ElAmrani`) ;
- **Groupe** : votre groupe, tel qu'il figure sur la liste de la classe.

Exemple : `12345678-ElAmrani-G2`. GitHub n'accepte ni les espaces ni les accents dans un nom de dépôt et les remplace par des tirets : vérifiez le nom final avant de valider. Communiquez le lien du dépôt (`https://github.com/votre-identifiant/12345678-ElAmrani-G2`) à l'enseignant avant la séance.

### Commits

Faites au moins trois commits pendant l'épreuve : après la description des données, après la modélisation, puis à la fin. Le dernier commit avant l'heure limite fait foi : marquez-le avec l'étiquette `remise-finale`.

### Arborescence conseillée

```
CodeApogee-Nom-Groupe/
├── README.md
├── requirements.txt
├── .gitignore
├── DECLARATION_IA.md
├── data/
│   ├── raw/                  # données brutes téléchargées (obligatoire, sauf exception ci-dessous)
│   └── processed/            # données préparées par le notebook
├── docs/
│   ├── fiche_sujet_FXX.md    # fiche de votre sujet
│   └── references.md         # sources consultées, avec liens
├── notebooks/
│   └── projet_FXX.ipynb      # notebook final, exécuté, avec ses sorties
├── src/                      # facultatif : téléchargement, fonctions réutilisées
│   └── telecharger_donnees.py
├── figures/                  # graphiques exportés pour le rapport et la présentation
├── rapport/
│   ├── rapport.pdf           # export PDF du notebook (compte rendu)
    └── rapport Latex
└── presentation/
    ├── presentation.pdf      # les six diapositives
    └── presentation.pptx     # fichier source (PowerPoint ou équivalent)
```

### Ressources à stocker dans le dépôt

| Ressource | Emplacement | Obligatoire |
| --- | --- | --- |
| Données brutes de votre sujet | `data/raw/` | Oui, sauf exception ci-dessous |
| Données préparées, si le notebook les enregistre | `data/processed/` | Si produites |
| Notebook final, exécuté, avec ses sorties | `notebooks/` | Oui |
| Graphiques utilisés dans le compte rendu et la présentation | `figures/` | Oui |
| Compte rendu (export PDF du notebook) | `rapport/` | Oui |
| Présentation de six diapositives, en PDF et en fichier source | `presentation/` | Oui |
| Fiche du sujet et références consultées | `docs/` | Oui |
| Scripts complémentaires (téléchargement, fonctions) | `src/` | Si utilisés |
| `README.md`, `requirements.txt`, `.gitignore`, `DECLARATION_IA.md` | Racine du dépôt | Oui |

**Exception pour les données.** Si la licence de la source interdit leur rediffusion, ou si un fichier dépasse 50 Mo (GitHub refuse les fichiers de plus de 100 Mo), placez dans `data/raw/` un script de téléchargement ou un fichier `LISEZMOI.md` donnant l'URL exacte et la date d'extraction. Le dépôt étant public, vérifiez les conditions d'utilisation de la source avant d'y déposer les données.

### Contenu minimal du README.md

1. Titre, auteur (nom, code Apogée, groupe), sujet (numéro F et titre) et résumé en trois lignes.
2. Problématique et principaux résultats, avec un petit tableau modèle contre référence.
3. Données : source, lien, licence, date d'extraction, et instructions pour les obtenir si elles ne sont pas dans le dépôt.
4. Installation : version de Python et commande `pip install -r requirements.txt`.
5. Exécution : ordre des fichiers à lancer et durée approximative.
6. Structure du dépôt.
7. Références et lien vers `DECLARATION_IA.md`.

### Exigences de reproductibilité

- Le notebook s'exécute **de bout en bout** après « Redémarrer et tout exécuter », sans erreur, et la version déposée contient ses sorties.
- Les chemins sont **relatifs**, par exemple avec `pathlib` : aucun chemin du type `C:\Users\...` ou `/content/drive/...`.
- Les **graines** sont fixées partout où intervient le hasard : découpage, modèles, NumPy, environnements Gymnasium.
- `requirements.txt` liste les bibliothèques **avec leurs versions**.
- Toutes les ressources du tableau ci-dessus sont présentes dans le dépôt, données comprises (sauf l'exception prévue).
- Le dépôt étant public, il ne contient **ni secret** (clé d'API, mot de passe, jeton) **ni donnée personnelle** confidentielle. Utilisez `.gitignore`.
- Les commits d'analyse sont datés entre le début et la fin de la séance. Un commit postérieur à l'heure limite n'est pas pris en compte.

## 10. Évaluation

### 10.1 Barème sur 20

Le notebook, compte rendu compris, vaut 13 points, les livrables 3 points et la soutenance 4 points.

| N° | Critère | Points | Attendu pour la note maximale | Erreurs qui coûtent des points |
| --- | --- | --- | --- | --- |
| **A** | **Notebook et compte rendu** | **13** |  |  |
| 1 | Sujet, problématique et objectif | 1 | Question précise ; objectif chiffré fixé avant les résultats ; nature du problème justifiée | Question vague ; objectif non mesurable |
| 2 | Jeu de données | 1,5 | Source, lien, licence, taille, unité d'observation, dictionnaire, cible et limites concrètes | Dictionnaire absent ; limites génériques |
| 3 | Exploration | 2 | Statistiques et graphiques pertinents, tous interprétés et reliés à la problématique | Graphiques sans commentaire ; axes sans unités |
| 4 | Préparation et prévention des fuites | 2 | Traitements justifiés ; pipeline ajusté sur l'apprentissage ; règles de la section 5.2 respectées ; alignement vérifié | Standardisation sur tout le jeu ; découpage aléatoire d'une série temporelle |
| 5 | Algorithme | 1,5 | Choix argumenté face à une alternative ; principe exact avec formule et symboles ; hyperparamètres expliqués | Description recopiée, sans lien avec le problème |
| 6 | Protocole d'évaluation | 2 | Découpage adapté ; référence naïve ; réglage en validation ; métriques justifiées ; test utilisé une seule fois | Pas de référence ; test utilisé pour régler le modèle |
| 7 | Résultats et interprétation | 2 | Comparaison chiffrée à la référence ; erreurs analysées ; surapprentissage discuté ; usage illustré sur des données non vues | Chiffres sans interprétation ; métrique trompeuse |
| 8 | Analyse critique, conclusion et rédaction | 1 | Limites réelles et pistes concrètes ; conclusion qui répond à la question ; compte rendu clair | Conclusion qui ne répond pas à la problématique |
| **B** | **Livrables** | **3** |  |  |
| 9 | Dépôt GitHub et reproductibilité | 2 | Toutes les exigences de la section 9 ; résultats retrouvés à l'identique | Notebook qui ne s'exécute pas ; ressources manquantes ; chemins absolus ; dépendances absentes |
| 10 | Diapositives | 1 | Six diapositives, structure respectée, lisibles, cohérentes avec le notebook | Diapositives surchargées ; chiffres différents du notebook |
| **C** | **Soutenance** | **4** |  |  |
| 11 | Présentation orale | 1 | Exposé clair, en 3 minutes au plus, messages principaux mis en avant | Lecture des diapositives ; dépassement du temps |
| 12 | Réponses aux questions et maîtrise | 3 | Explique son code et ses choix, modifie et relance une cellule, interprète correctement, reconnaît les limites | Incapacité à expliquer une partie de son travail |
|  | **Total** | **20** |  |  |

### 10.2 Pénalités

- Commit postérieur à l'heure limite : non pris en compte ; seul le dernier commit dans les temps est corrigé.
- Dépôt privé ou nom non conforme à `CodeApogee-Nom-Groupe` : 0,5 point.
- Nombre de diapositives différent de six : 0,5 point.
- Un chiffre du compte rendu ou de la présentation qui n'apparaît pas dans les sorties du notebook n'est pas crédité.
- Code d'analyse présent dans le dépôt avant le début de la séance : la partie concernée n'est pas notée, sans préjudice des règles d'intégrité de la section 11.

### 10.3 Déroulement de la soutenance

La soutenance a lieu lors de la séance suivante et dure **8 minutes** par étudiant :

- 3 minutes de présentation des six diapositives, sans interruption ;
- 5 minutes de questions, pendant lesquelles l'enseignant peut vous demander d'ouvrir le notebook, d'expliquer une cellule, de modifier un paramètre et de relancer le calcul.

Venez avec votre notebook ouvert et exécuté, et votre dépôt accessible.

### 10.4 Exemples de questions orales

1. **Données.** Que représente une ligne de votre jeu de données après préparation ? Montrez-en une.
2. **Données.** Pourquoi avez-vous traité les valeurs manquantes ou atypiques de cette façon ? Qu'aurait changé un autre choix ?
3. **Préparation.** Montrez dans le code où la standardisation ou l'encodage est ajusté. Sur quelles données ?
4. **Préparation.** Comment prouvez-vous qu'aucune variable n'utilise une information postérieure à la date de prédiction ?
5. **Algorithme.** Expliquez le principe de votre algorithme et chaque symbole de la formule de votre compte rendu.
6. **Algorithme.** Quels paramètres sont appris, lesquels avez-vous fixés ? Modifiez un hyperparamètre et commentez l'effet.
7. **Algorithme.** Pourquoi cet algorithme plutôt qu'un autre du support ?
8. **Évaluation.** Pourquoi cette métrique principale ? Quelle valeur obtient votre référence naïve, et pourquoi ?
9. **Évaluation.** Combien de configurations avez-vous essayées ? Le jeu de test a-t-il servi à choisir ?
10. **Résultats.** Votre modèle surapprend-il ? Sur quels éléments vous appuyez-vous ?
11. **Résultats.** Commentez une erreur précise de votre modèle : où se trompe-t-il le plus ?
12. **Non supervisé.** Comment savez-vous que vos groupes ou vos anomalies ne dépendent pas de la graine ou de la période ?
13. **Critique.** Votre conclusion tiendrait-elle avec une autre période de test ?
14. **Reproductibilité.** Je clone votre dépôt sur une autre machine : que dois-je faire pour retrouver exactement vos chiffres ?
15. **Outils d'IA.** Quelles parties avez-vous réalisées avec un outil d'IA, et comment avez-vous vérifié le résultat ?

## 11. Authenticité, ressources externes et outils d'IA

**Principe.** Vous devez pouvoir expliquer et défendre chaque partie de votre travail, code compris. Tout ce qui ne vient pas de vous est déclaré.

### Autorisé pendant l'épreuve, à condition d'être déclaré

- Le support du cours, vos notes personnelles, la documentation officielle des bibliothèques (pandas, scikit-learn, etc.).
- Les outils d'IA générative pour comprendre un message d'erreur, une notion ou une fonction, ou pour obtenir une suggestion de code que vous lisez, testez et adaptez.

### Interdit

- Communiquer avec un autre étudiant, ou partager du code, des résultats ou des fichiers.
- Consulter le dépôt d'un autre étudiant pendant l'épreuve. Les dépôts sont publics : une consultation est assimilée à une copie, et les dates des commits permettent de la repérer.
- Écrire le code d'analyse avant la séance.
- Remettre du code, des analyses ou des interprétations que vous ne comprenez pas, quelle qu'en soit la source.
- Inventer, arrondir à votre avantage ou modifier des résultats.
- Utiliser une ressource ou un outil d'IA sans le déclarer.

### Déclaration obligatoire

Remplissez le fichier `DECLARATION_IA.md` du dépôt et recopiez-le en dernière section du notebook. Si vous n'avez utilisé aucun outil d'IA, écrivez-le.

| Outil ou ressource | Version ou date | Usage précis | Parties concernées | Vérification effectuée |
| --- | --- | --- | --- | --- |
| *Exemple : assistant d'IA* | *[nom, date]* | *Explication d'une erreur de dimension dans le pipeline* | *Notebook, section 4* | *Correction testée, sorties comparées avant et après* |

### Conséquences

- En soutenance, une partie que vous ne savez pas expliquer peut perdre tout ou partie des points qui lui correspondent, même si elle est correcte à l'écrit.
- Une utilisation non déclarée, une copie ou des résultats inventés relèvent du règlement de l'établissement sur l'intégrité académique.

## 12. Checklist finale avant remise

**Avant la séance**

- [ ] Dépôt GitHub **public** nommé `CodeApogee-Nom-Groupe`, avec ses dossiers et un README à compléter ; lien communiqué à l'enseignant
- [ ] Données téléchargées dans `data/raw/`, date d'extraction notée ; fiche du sujet dans `docs/`
- [ ] Environnement testé : les imports du support s'exécutent sans erreur

**Notebook et compte rendu**

- [ ] En-tête rempli : sujet, problématique, objectif mesurable, nature du problème
- [ ] Source, lien, licence et date d'extraction indiqués ; dictionnaire des principales variables
- [ ] Au moins trois graphiques, chacun suivi de son interprétation
- [ ] Transformations dans un pipeline ajusté sur l'apprentissage ; découpage chronologique si les données sont datées
- [ ] Référence naïve et modèle comparés sur le test, utilisé une seule fois
- [ ] Erreurs analysées et usage illustré sur des observations non vues
- [ ] Les dix sections du plan imposé présentes ; conclusion qui répond à la problématique
- [ ] « Redémarrer et tout exécuter » fonctionne sans erreur ; notebook exporté en `rapport/rapport.pdf`

**Présentation**

- [ ] Exactement six diapositives, dans l'ordre imposé, en PDF
- [ ] Mêmes chiffres que dans le notebook

**Dépôt GitHub**

- [ ] Toutes les ressources présentes : données, notebook exécuté, figures, `rapport.pdf`, présentation (PDF et source), fiche du sujet et références
- [ ] README complété, `requirements.txt` avec versions, `DECLARATION_IA.md`
- [ ] Chemins relatifs, graines fixées, aucun secret ni donnée personnelle
- [ ] Au moins trois commits pendant la séance ; dernier commit étiqueté `remise-finale` avant l'heure limite

## Annexe A : les 29 algorithmes du support

La numérotation est celle du notebook `Tp_ML.ipynb`, qui compte bien 29 sections. Les forêts aléatoires et le gradient boosting y figurent deux fois, en régression et en classification.

| N° | Algorithme | Famille | Mise en œuvre dans le support |
| --- | --- | --- | --- |
| 1 | Régression linéaire | Supervisé, régression | `LinearRegression` |
| 2 | Ridge | Supervisé, régression | `Ridge` |
| 3 | Lasso | Supervisé, régression | `Lasso` |
| 4 | Régression polynomiale | Supervisé, régression | `PolynomialFeatures` puis `Ridge` |
| 5 | Arbre de régression | Supervisé, régression | `DecisionTreeRegressor` |
| 6 | Forêt aléatoire (régression) | Supervisé, régression | `RandomForestRegressor` |
| 7 | Gradient Boosting (régression) | Supervisé, régression | `HistGradientBoostingRegressor` |
| 8 | Régression logistique | Supervisé, classification | `LogisticRegression` |
| 9 | KNN | Supervisé, classification | `KNeighborsClassifier` |
| 10 | Naive Bayes | Supervisé, classification | `GaussianNB` |
| 11 | Arbre de décision | Supervisé, classification | `DecisionTreeClassifier` |
| 12 | Forêt aléatoire (classification) | Supervisé, classification | `RandomForestClassifier` |
| 13 | SVM | Supervisé, classification | `SVC` (noyau RBF) |
| 14 | Gradient Boosting (classification) | Supervisé, classification | `HistGradientBoostingClassifier` |
| 15 | AdaBoost | Supervisé, classification | `AdaBoostClassifier` |
| 16 | XGBoost | Supervisé, classification | `XGBClassifier` |
| 17 | K-means | Non supervisé, partitionnement | `KMeans` |
| 18 | Classification hiérarchique (CAH) | Non supervisé, partitionnement | `AgglomerativeClustering` (lien de Ward) |
| 19 | DBSCAN | Non supervisé, partitionnement | `DBSCAN` |
| 20 | Mélanges gaussiens | Non supervisé, partitionnement | `GaussianMixture` |
| 21 | ACP | Non supervisé, réduction de dimension | `PCA` |
| 22 | t-SNE | Non supervisé, réduction de dimension | `TSNE` |
| 23 | UMAP | Non supervisé, réduction de dimension | `umap.UMAP` |
| 24 | Isolation Forest | Non supervisé, détection d'anomalies | `IsolationForest` |
| 25 | Bandits manchots | Renforcement | Simulation à 4 bras, programmée à la main |
| 26 | Epsilon-greedy | Renforcement | Simulation à 4 bras, programmée à la main |
| 27 | Q-learning | Renforcement | Q-learning tabulaire sur Taxi (Gymnasium) |
| 28 | SARSA | Renforcement | Environnement Taxi (Gymnasium) |
| 29 | DQN | Renforcement | Calcul conceptuel d'une cible de Bellman, sans réseau entraîné |

## Annexe B : modèle d'en-tête du notebook

À recopier dans la première cellule de texte du notebook et à remplir pendant les dix premières minutes. Les titres suivants reprennent le plan imposé du compte rendu (section 7).

```markdown
# [Numéro F et titre du sujet]

**Nom et prénom :** ...    **Code Apogée :** ...    **Groupe :** ...    **Filière :** S7 FIN / S7 CI    **Date :** ...

**Dépôt GitHub :** https://github.com/votre-identifiant/CodeApogee-Nom-Groupe

## 1. Sujet et problématique
- **Intérêt du sujet** (2 à 3 lignes) : ...
- **Problématique** (une question) : ...
- **Objectif mesurable** (métrique, référence, période de test, seuil) : ...
- **Nature du problème** (et pourquoi) : ...
- **Algorithme principal envisagé** (n° de l'annexe A) : ...

## 2. Jeu de données
## 3. Exploration
## 4. Préparation
## 5. Algorithme
## 6. Protocole expérimental
## 7. Résultats
## 8. Analyse critique
## 9. Conclusion
## 10. Références et reproduction
## Déclaration des ressources et outils d'IA
```
