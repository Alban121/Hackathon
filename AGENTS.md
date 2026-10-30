# AGENTS.md — Hackathon ML 2026

Consignes pour tout assistant IA (Claude, Copilot, ChatGPT…) qui travaille dans ce dépôt.
Source : `ressources/hackathon_briefing_EN.pdf`. En cas de doute, le sujet fait foi.

## Le sujet

- Prédire l'intensité d'un entraînement sportif : `easy`, `moderate` ou `hard`.
- L'intensité est mesurée par les capteurs de l'appli **séparément pour chaque personne** :
  « hard » veut dire difficile *pour cette personne*. Comprendre ce que cela implique fait partie du problème.
- Les trois classes sont à peu près équilibrées.
- Métrique : **macro-F1** (F1 calculé par classe puis moyenné). Toujours sur 3 classes : ignorer une classe coûte un tiers du score.
- Leaderboard Kaggle : public = 50 % du test ; le classement final se fait sur l'autre moitié (privée).
  Ne pas sur-optimiser le score public.

## Organisation du dépôt

| Chemin | Contenu |
| --- | --- |
| `data/train.csv` | ~22 700 entraînements avec la cible `intensity` |
| `data/test.csv` | ~7 700 entraînements à prédire (sans `intensity`) |
| `data/sample_submission.csv` | Format attendu : `workout_id,intensity` |
| `notebook.ipynb` | Notebook de l'équipe (à rendre), chemins relatifs à la racine |
| `submissions/` | Fichiers CSV envoyés sur Kaggle |
| `LOG.md` | Journal des soumissions (à rendre) |
| `ressources/` | Sujet PDF, notebook de départ et modèle de LOG, à ne pas modifier |

Les données ne sont pas modifiées à la main : tout prétraitement se fait dans le code.

## Règles du hackathon (à respecter strictement)

Autorisé :
- Tout modèle scikit-learn **qui n'est pas un réseau de neurones** : régression logistique, k-NN, SVM,
  naive Bayes, arbres, random forest, extra trees, HistGradientBoosting, voting, stacking…
- pandas, NumPy, matplotlib.
- Les assistants d'IA générative, dans une **nouvelle conversation**.

Interdit :
- Le deep learning, **y compris `MLPClassifier`**.
- Par prudence, pas de XGBoost, LightGBM ou CatBoost : le sujet n'autorise que scikit-learn, pandas, NumPy et matplotlib.
- Les données externes.
- Le partage de code entre équipes.
- Plus de **15 soumissions Kaggle** par équipe.

Si une demande enfreint une de ces règles, l'assistant le signale et propose une alternative autorisée.

## Façon de travailler

- « Think first, then prompt » : l'équipe réfléchit avant de demander du code. L'assistant explique
  ses choix et le code qu'il produit, pour que **chaque membre puisse expliquer le modèle final sur papier**.
- Préférer un code simple, lisible et commenté à un code astucieux.
- Chaque décision se valide avec la fonction `evaluate` (macro-F1 sur un jeu de validation),
  jamais uniquement avec le score public.
- Comparer **au moins 3 familles de modèles** sur la validation.
- Fixer les graines aléatoires (`random_state`) pour que les résultats soient reproductibles.

## LOG.md

- **Une ligne par soumission Kaggle**, remplie **avant** de regarder le score (sauf la colonne « Public score »).
- Colonnes : Time, Who (codes participants), What changed, Why we expect it to help, Validation macro-F1, Public score.
- Utiliser uniquement les **codes participants**, jamais de noms.
- Gate 2 (17:35) : ajouter une matrice de confusion et une phrase d'analyse des classes confondues.
- Bonus : la meilleure idée notée dans LOG.md vaut +0,5.

## Soumission Kaggle

- Format : `workout_id,intensity`, une ligne par entraînement du test (~7 670 lignes).
- Équipe Kaggle : **Team_13** (nom officiel obligatoire). Aucune soumission avant que l'équipe Kaggle soit complète.
- À 18:10 : sélectionner la soumission finale sur Kaggle, déposer notebook + LOG.md sur Boostcamp.

## Marqueurs de conversation IA

À taper dans la conversation quand c'est annoncé : `#START <code> Hackathon ML 2026` (13:50),
`#CHECKPOINT-1` (15:50), `#CHECKPOINT-2` (16:20), `#CHECKPOINT-3` (17:35), `#END` (18:10).
Les conversations sont partagées après `#END`. Ne pas y mettre d'informations personnelles.

## Planning (30 octobre)

| Heure | Étape |
| --- | --- |
| 14:20 | Sprint 1 |
| 15:50 | Gate 1 (seuil G1 révélé) + pause |
| 16:20 | Indice 1 (gratuit), Sprint 2 ; indices 2 et 3 payants (−0,5 et −1 point) |
| 17:35 | Gate 2 et Gate 3 (seuils G2, G3 révélés) |
| 18:10 | Fermeture Kaggle, rendu |
