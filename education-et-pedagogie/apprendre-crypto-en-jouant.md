# CryptoQuest — comprendre la crypto en jouant

**Statut : idée non démarrée.** Application pédagogique ludique, **distincte** du laboratoire historique `bitcoin-wallet-education-lab` (scripts clés/portefeuille) et de la future interface d'achat BTC. Aucun fonds réel requis.

## But
Expliquer pas à pas les mécanismes fondamentaux des cryptomonnaies **sans pousser à investir** : blockchain, clés publiques/privées, signatures, transactions, frais réseau, consensus, custodial/non-custodial, risques, smart contracts, stablecoins, arnaques, volatilité et sécurité.

## Boucle de jeu
- Petites missions de 3 à 7 minutes, une notion = une expérience interactive.
- Exemple 1 : signer une transaction fictive puis vérifier la signature ; la clé privée ne doit jamais être partagée.
- Exemple 2 : choisir des frais pour une file de transactions simulée et constater délai/coût.
- Exemple 3 : reconnaître une tentative de phishing et observer la conséquence dans un environnement sans fonds.
- Exemple 4 : faire tourner des rôles de nœuds/miners/validateurs simplifiés ; comparer sécurité et compromis.
- Quiz de prédiction « que se passe-t-il si… ? », correction expliquée et révision espacée.
- Débloquer badges, niveaux et « outils de compréhension », pas de token échangeable.

## MVP
5 chapitres (clés, transactions, frais, conservation, arnaques), moteur de scénario déterministe, simulation visuelle locale, quiz à feedback immédiat, progression sans compte. Aucun wallet connecté, paiement ou transaction sur réseau réel.

## Qualité et rigueur
Séparer **modèle pédagogique simplifié** et fonctionnement réel ; marquer les simplifications. Éviter les affirmations comme « toute transaction est gratuite » ou « la blockchain est anonyme ». Tests utilisateurs : expliquer sans jargon et vérifier la compréhension différée plutôt que le seul clic de bonne réponse.

## Architecture candidate
Frontend web/PWA accessible mobile, scénarios JSON versionnés, simulations pures et testables sans blockchain, sauvegarde locale ; serveur et comptes uniquement si nécessité prouvée. Plusieurs parcours selon novice, collégien/adulte, technique, culture financière.

## Risques
Apparence de conseil financier, gamification de prises de risques, publicité crypto cachée, données de mineurs, références réglementaires périssables. Simulations uniquement avec unités fictives ; encarts risques et sécurité. Pas de connexion d'échange dans le parcours pédagogique.

## Étude avant départ
Benchmark d'applications d'apprentissage existantes, entretien avec 5 novices, conception de 2 prototypes papier, pré-test/post-test de compréhension. Ouvrir le dépôt dédié avant expérimentation et retirer la fiche de l'incubateur.

## À trancher
Public exact, niveau mathématique, Android natif vs web, ton humoristique vs sérieux, éventuellement open-source et traduction multilingue.
