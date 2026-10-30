# Décisions — Team_13

Ce fichier trace les choix de fonctionnement et d'architecture, et **pourquoi** on les a faits.
Il sert à préparer la fiche d'explication (18:20, sur papier, sans ordinateur).
`LOG.md` dit *ce qu'on a soumis*. Ce fichier-ci dit *pourquoi on a fait ces choix*.

## 1. Synthèse pour la fiche d'explication

_À remplir à la fin. C'est ce que chaque membre doit savoir expliquer sans notes._

- **Modèle final :** …
- **Features utilisées, et pourquoi :** …
- **Comment on a validé :** …
- **Ce qui a le plus aidé :** …
- **Ce qui n'a pas marché, et pourquoi :** …
- **Les classes les plus confondues (matrice de confusion) :** …
- **Ce qu'on ferait avec plus de temps :** …

## 2. Journal des décisions

Une entrée par décision. Format : contexte, options envisagées, choix, raison, résultat.

### D1 — Organisation du dépôt (setup)
- **Contexte :** il faut un dépôt clair et partagé avant le sprint 1.
- **Choix :**
  - `data/` pour les CSV Kaggle, `ressources/` pour le sujet.
  - `notebook.ipynb` comme notebook d'équipe, `submissions/` pour les CSV envoyés.
  - `LOG.md` pour les soumissions, `DECISIONS.md` pour le raisonnement.
- **Raison :** le rendu demande notebook + LOG.md. Avoir un seul notebook évite les versions divergentes.

### D2 — Bibliothèques autorisées
- **Contexte :** le sujet autorise « tout modèle scikit-learn qui n'est pas un réseau de neurones », ainsi que pandas, NumPy et matplotlib.
- **Options :** scikit-learn seul, ou ajouter XGBoost/LightGBM.
- **Choix :** scikit-learn seul.
- **Raison :** XGBoost et LightGBM sont hors de scikit-learn, donc c'est un risque pour la note. `HistGradientBoostingClassifier` est autorisé et repose sur le même principe.

<!-- Modèle pour une nouvelle entrée :
### Dn — Titre court (heure)
- **Contexte :**
- **Options envisagées :**
- **Choix :**
- **Raison :**
- **Résultat (validation macro-F1) :**
-->
