---
theme: seriph
background: https://images.unsplash.com/photo-1500937386664-56d1ced41ca1?q=80&w=2070&auto=format&fit=crop
class: text-center
highlighter: sitter
lineNumbers: false
drawings:
  enabled: true
transition: slide-left
title: Analyse de la Sous-Alimentation Mondiale
---

# Analyse et Prédiction de la Sous-Alimentation Mondiale

<!-- Le Logo FAO (assure-toi qu'il est dans le dossier public/ de ton projet) -->
<img src="./FAO_logo.svg" class="w-32 mb-8 drop-shadow-lg" alt="Logo FAO">
### Transformer des données fragmentées en une vision globale
  
  

**Présenté par Johan**  
*Data Analyst Trainee*



---
layout: default
---

# 🎯 L'Objectif du Projet

**Le Problème :**
L'accès à l'information alimentaire est fragmenté. Les données sur la sous-alimentation sont incomplètes, créant des "zones d'ombre" géographiques (pays sans données déclarées).

**La Mission :**
1. **Nettoyer** des sources de données hétérogènes.
2. **Modéliser** les relations entre ressources (calories/protéines) et sous-alimentation.
3. **Prédire** les taux manquants pour obtenir une cartographie mondiale sans interruption.

---
layout: default
---

# 🛠️ Étape 1 : Le Défi des Données

<div class="grid grid-cols-2 gap-4">
<div>

### L'état initial (Data Audit)

* Sources multiples (CSV).
* Colontynes mal typées (`object` vs `float`).
* Valeurs incohécompressibles (`<0.1`).
* Absence de continuité géographique.

</div>

<div class="p-4 border border-red-500 rounded bg-red-50/10">

#### 📊 Résumé du Diagnostic

| Indicateur | Statut | Action |
| :--- | :---: | :--- |
| Complétude | ⚠️ ALERTE | Nettoyage des colonnes vides |
| Cohérence | ❌ ERREUR | Conversion des types (String $\rightarrow$ Float) |
| Géographie | ⚠️ ALERTE | Filtrage des zones communes |

</div>
</div>

---

# ⚙️ Étape 2 : La Transformation

### Du "Poids Global" à l' "Indicateur par habitant"

Pour rendre les pays comparables, j'ai réinventé la donnée :

*   **Standardisation :** Harmonisation des noms de zones (FAO $\rightarrow$ ISO3).
*   **Feature Engineering :** 
    *   $\text{Production} \rightarrow \text{Production par habitant}$
    *   $\text{Import/Export} \rightarrow \text{Flux par habitant}$
*   **Imputation Intelligente :** Remplacement des valeurs indéterminées (`<0.1`) par une valeur métier (0.001) pour préserver la structure statistique.

---
layout: two-cols
---

# 📊 Étape 3 : L'Analyse Statistique

### Identifier les leviers de nutrition

L'analyse des corrélations permet d'isoler les variables qui impactent réellement le taux de sous-alimentation.

::right::

<div class="ml-4">

<!-- Affichage de la heatmap -->
![Matrice de Corrélation](./heatmap.png)

<p class="text-xs italic text-gray-500 mt-2">
  Matrice de Corrélation : Identification des variables clés
</p>

</div>

---

# 🤖 Étape 4 : Le Modèle Prédictif

### Algorithme : Random Forest Regressor

**Architecture du Pipeline :**
1. **Imputation :** Médiane pour les valeurs manquantes.
2. **Scaling :** Standardisation des données (StandardScaler).
3. **Régression :** Forêt aléatoire optimisée via `GridSearchCV`.

<div class="grid grid-cols-2 gap-4 mt-4">

<!-- Colonne 1 : Erreurs -->
<div class="p-2 border border-blue-500 rounded flex flex-col items-center">

<img src="./erreurs_distrib.png" class="w-37 h-auto object-contain" alt="Évaluation de l'erreur">
<p class="text-[10px] text-center mt-2">Évaluation de l'erreur (Distribution des résidus)</p>

</div>

<!-- Colonne 2 : Performance -->
<div class="p-2 border border-green-500 rounded flex flex-col items-center">

<img src="./delta_reel_predit.png" class="w-39 h-auto object-contain" alt="Performance : Réel vs Prédit">
<p class="text-[10px] text-center mt-2">Performance : Réel vs Prédit</p>

</div>

</div>
---
layout: default
---

# 🌍 Le Réassemblage Final

<div style="display: flex; flex-direction: column; align-items: center; justify-content: center; width: 100%;">

<!-- On utilise l'élément HTML img standard avec un chemin direct -->
<img src="./carto_global.png" style="max-width: 78%; max-height: 60vh; object-fit: contain; border: 2px solid white; border-radius: 8px;" alt="Ma Carte">

<p style="color: white; font-size: 1.2rem; margin-top: 20px; text-align: center;">
  Cartographie complète intégrant les données réelles et les prédictions
</p>

</div>

---
layout: default
---

# 🚀 Conclusion & Perspectives

**Ce que j'ai accompli :**
* ✅ Un pipeline automatisé de nettoyage à la prédiction.
* ✅ Une unification des données mondiales par habitant.
* ✅ Une estimation fiable des zones auparavant inaccessibles.

**Pour aller plus loin :**
* 📈 **Données Macro :** Intégrer le PIB et l'indice de développement humain (IDH).
* ⚠️ **Contexte Géopolitique :** Modéliser l'impact des conflits et des crises sanitaires sur la disponibilité alimentaire.
* ⚖️ **Précision Statistique :** Affiner l'imputation des valeurs '<0.1' pour qu'elle soit proportionnelle à la taille de la population (éviter les biais sur les petits États).

---
layout: center
class: text-center
---

# Merci de votre attention !
## Des questions ?