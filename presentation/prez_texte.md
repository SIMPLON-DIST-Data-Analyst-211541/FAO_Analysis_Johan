# 🎤 Script de Présentation Orale : Analyse de la Sous-Alimentation



---

## 1. Introduction (Le Contexte)
Bonjour à tous. Aujourd'hui, je vais vous présenter mon projet d'analyse sur la sécurité alimentaire mondiale. 

Le défi de départ est un problème classique en Data Science : nous avons énormément de données sur la production agricole, animale et la population, mais ces informations sont parsemées de 'trous'. Certains pays ne transmettent pas leurs chiffres sur la sous-alimentation, ce qui rend impossible d'avoir une vision globale et juste de la situation mondiale sur une simple carte.

---

## 2. Les Obstacles (La Problématique)
En plongeant dans les données, j'ai rencontré trois obstacles majeurs qui ont dicté ma méthodologie :

1.  **L'hétérogrité des sources :** Les fichiers ne parlaient pas tous la même langue. Les noms des pays variaient d'un tableau à l'autre et les unités de mesure n'étaient pas uniformes.
2.  **La qualité des données :** J'ai trouvé énormément de valeurs manquantes ou mal formatées, comme des écritures du type '<0.1', ce qui empêchait tout calcul mathématique immédiat.
3.  **Le problème d'échelle :** Comparer un immense pays comme la Chine avec un petit État insulaire est impossible si l'on regarde uniquement les tonnes de nourriture produites. Il faut transformer ces données pour regarder ce que chaque habitant peut réellement consommer.

---

## 3. La Méthodologie (La Solution)
Pour surmonter cela, j'ai mis en place une démarche en trois étapes :

*   **Premièrement, un nettoyage rigoureux :** J'ai harmonisé les noms des pays et transformé les données brutes en indicateurs **par habitant** (comme la production de nourriture par personne). Cela permet de mettre tous les pays sur un pied d'égalité pour l'analyse.
*   **Deuxièmement, une phase d'apprentissage :** J'ai utilisé l'intelligence artificielle. J'ai entraîné un modèle informatique à 'apprendre' la relation entre la disponibilité des ressources (calories, protéines) et le taux de sous-alimentation des pays qui possèdent des données complètes.
*   **Enfin, la prédiction :** Une fois que le modèle a compris ces liens, je l'ai utilisé pour estimer intelligemment les chiffres manquants pour les zones restantes.

---

## 4. Conclusion et Perspectives (La Valeur Ajoutée)
Le résultat est une carte du monde complète et cohérente. Grâce à ce travail, nous ne voyons plus de 'zones blanches' sur la carte : nous avons une vision continue de l'état de la sous-alimentation mondiale.

Bien sûr, ce modèle est une première étape. Pour aller plus loin, on pourrait enrichir cette analyse en intéant des données macroéconomiques ou des indicateurs de crises politiques et sanitaires, qui sont des facteurs clés impactant directement la capacité d'un pays à nourrir sa population.


Merci de votre attention.