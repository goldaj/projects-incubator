# TRAME — langage génératif pour les courbes de marché

**Statut : recherche scientifique en cours, avec protocoles et audits sur données réelles. Aucun modèle entraîné ni performance prédictive démontrée.**

## Question et périmètre

Peut-on représenter causalement les observations de plusieurs marchés comme un langage, puis apprendre leur évolution avec une architecture générative de type GPT ? La question porte sur la prédiction des prix bruts et sur le choix de représentation. Elle est distincte du développement d'un bot de trading, de ses frais et de son exploitation.

## Livrables existants

- Quatorze documents dans l'édition2.4, dossier de102pages et synthèse de trois pages.
- Comparaisons de langages, protocole candidat, corpus, contrôles arithmétiques et journaux de version.
- Audit de reconstruction sur304920présentations de cibles historiques, correspondant à15360cotations distinctes : il vérifie un codec, sans prouver une prédiction.
- Sources modifiables et scripts ; les données brutes restent locales tant que leur redistribution n'est pas vérifiée.

## Source de vérité et prochaine étape

[Dépôt TRAME](https://github.com/goldaj/trame-chartist-research). La prochaine étape est de qualifier les primitives numériques, les scores en prix bruts et les contrôles de simulation avant entraînement. Les protocoles peuvent encore être révisés ; les résultats négatifs sont conservés.

Le projet reste indépendant de `hyperliquid-btc-pilot`. La documentation ne promet pas une stratégie rentable et ne déclenche aucun ordre.
