# Expériences de modèles de prix crypto

**Stade : code de recherche exploratoire retrouvé et archivé, sans résultat prédictif validé.**

Le projet rassemble collecte et préparation de séries Binance/CryptoCompare, indicateurs, modèles linéaires, forêts et architectures neuronales historiques, ainsi qu'un petit affichage Tkinter. Les anciens tests et variantes sont conservés dans une structure explicite.

Les sources nettoyées ont leur dépôt privé `crypto-price-ml-experiments`. Les clés, datasets, modèles et résultats personnels restent hors Git. La préparation a vérifié la syntaxe et la configuration, sans entraîner de modèle ni ouvrir un compte ou exécuter les anciens tests réseau.

Prochaines étapes : figer les dépendances, séparer tests unitaires et collecte, revoir les découpages chronologiques et fuites de cible, documenter les métriques et les droits des données avant une version publique reproductible.

## Revue scientifique 2026-10-25

La [PR #1 du dépôt privé](https://github.com/goldaj/crypto-price-ml-experiments/pull/1)
documente les fuites potentielles vérifiées dans les scripts historiques
(étiquette terminale artificielle, imputation avant séparation temporelle)
et ajoute une baseline causale testée sur valeurs fictives, séparée
des anciens réseaux. Aucune prédiction ou profit démontré.
