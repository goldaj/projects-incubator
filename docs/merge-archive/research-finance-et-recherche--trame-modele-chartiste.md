# TRAME — langage génératif pour les courbes de marché

**Statut : recherche scientifique en cours, avec protocoles et audits sur données réelles. Aucun modèle entraîné ni performance prédictive démontrée.**

## Question et périmètre

Peut-on représenter causalement les observations de plusieurs marchés comme un langage, puis apprendre leur évolution avec une architecture générative de type GPT ? La question porte sur la prédiction des prix bruts et sur le choix de représentation. Elle est distincte du développement d'un bot de trading, de ses frais et de son exploitation.

## Livrables existants

- Quatorze documents dans l'édition 2.4, dossier de 102 pages et synthèse de trois pages.
- Comparaisons de langages, protocole candidat, corpus, contrôles arithmétiques et journaux de version.
- Audit de reconstruction sur 304 920 présentations de cibles historiques, correspondant à 15 360 cotations distinctes : il vérifie un codec, sans prouver une prédiction.
- Sources modifiables et scripts ; les données brutes restent locales tant que leur redistribution n'est pas vérifiée.

## Source de vérité et prochaine étape

[Dépôt TRAME](https://github.com/goldaj/trame-chartist-research). La prochaine étape est de qualifier les primitives numériques, les scores en prix bruts et les contrôles de simulation avant entraînement. Les protocoles peuvent encore être révisés ; les résultats négatifs sont conservés.

Le projet reste indépendant de `hyperliquid-btc-pilot`. La documentation ne promet pas une stratégie rentable et ne déclenche aucun ordre.

## Revue scientifique 2026-10-25

La [PR #1 du dépôt autonome](https://github.com/goldaj/trame-chartist-research/pull/1)
propose désormais un scoreur de **prévisions en prix natifs** comparées
à la persistance, sur jeux de tests synthétiques, ainsi qu'un protocole
prospectif de validation. Elle ne valide ni un modèle, ni un avantage
prédictif, ni un bot de trading. Le protocole antérieur gelé est inchangé.
