# Présentation du Projet : Analyse et Prédiction de la Sous-Alimentation Mondiale

## 🎯 Objectif du Projet
L'objectif est d'analyser les facteurs influençant le taux de sous-alimentation par pays et de construire un modèle prédictif capable d'estimer ce taux pour les zones où les données sont manquantes, afin d'obtenir une cartographie mondiale complète.

---

## 🛠️ Étapes Clés & Méthodologie

### 1. Acquisition et Audit des Données (Data Auditing)
*   **Sources :** Multiples fichiers CSV (Population, Sous-alimentation, Production végétale/animale).
*   **Problématique :** Hétérogénéité des formats, présence de valeurs manquantes massives et incohérences de types.
*   **Actions :** 
    *   Vérification de la cohérence des clés de fusion (Codes Zones, Produits, Éléments).
    *   Audit de la complétude (détection des colonnes peu informatives à supprimer).

### 2. Nettoyage et Préparation (Data Cleaning & Engineering)
*   **Gestion des anomalies :** 
    *   Traitement des valeurs "<0.1" dans les données de sous-alimentation par une imputation métier (0.001) pour éviter de fausser les statistiques des petits États.
    
*   **Standardisation :** 
    *   Filtrage temporel : Focus sur l'année de référence **2013** pour assurer la comparabilité.
    *   Nettoyage géographique : Suppression des pays absents de l'un des datasets pivots pour garantir une base d'étude homogène (élimination des 29 pays manquants).
    
*   **Feature Engineering (Création de variables) :** 
    *   Transformation des données globales en **données par habitant** (Production/hab, Import/hab, Export/hab) pour rendre les indicateurs comparables entre grands et petits pays.
    *   Calcul d'un nouvel indicateur cible : `Pop sous-alimentée %`.

### 3. Analyse Exploratoire (EDA)
*   **Découverte de corrélations :** Utilisation de matrices de corrélation pour identifier les leviers (Disponibilité calorique, protéines, etc.).
*   **Analyse de distribution :** Identification du bruit dans certaines colonnes (ex: 'Production par hab') ayant conduit à leur simplification.

### 4. Modélisation (Machine Learning)
*   **Pipeline de traitement :** Imputation des valeurs manquantes (médiane) et Standardisation (StandardScaler).
*   **Stratégie d'optimisation :** Utilisation de `GridSearchCV` pour tester plusieurs algorithmes (Linear Regression, Ridge, Lasso, Random Forest) et hyperparamètres.
*   **Gestion du Surapprentissage (Overfitting) :** 
    *   Problème initial : Modèle trop complexe avec un écart massif Train/Test.
    *   Solution : Réduction de la profondeur des arbres (`max_depth`) et augmentation de la contrainte sur les feuilles (`min_samples_leaf`).

---

## 📈 Résultats & Conclusions

### Performance du Modèle Final
*   **Algorithme :** `RandomForestRegressor` optimisé.
*   **Score R² (Test) :** ~75% (Le modèle explique 75% de la variance observée sur les données de test).
*   **Stabilité :** Réduction significative de l'écart entre l'erreur d'entraînement et l'erreur de test.

### Visualisation Finale
*   Génération d'une **carte choroplèthe mondiale** (via Plotly) combinant les données réelles et les prédictions pour une vision globale et sans "trous" géographiques.

### 💡 Pistes d'Amélioration (Perspectives)
1.  **Enrichissement des données :** Intégration de variables macroéconomiques (PIB, indice de développement humain).
2.  **Contexte Géopolitique :** Ajout de variables binaires pour marquer les zones de conflit ou d'épidémies (facteurs de rupture de la disponibilité alimentaire).
3.  **remplacement de la valeur '<0.1' :** Affiner la valeur choisie de sorte à l'adapter en pourcentage de la population, des petits pays comme des grands