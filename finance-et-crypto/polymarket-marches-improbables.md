# Polymarket Oddity Scanner — détecter les marchés « absurdes »

**Statut : idée logicielle non démarrée.** Scanner analytique de marchés prédictifs, non un système de paris automatiques. **Point bloquant : la France figure dans les territoires interdits de trading Polymarket au 26 octobre 2026. Ne pas tenter de contourner les restrictions géographiques, même via un VPN.** Consulter https://help.polymarket.com/en/articles/13364163-geographic-restrictions .

## Vision
Explorer automatiquement les marchés aux intitulés invraisemblables ou amusants : « Jésus revient-il sur Terre cette année ? », prédictions extravagantes, marchés à faible probabilité, critères de résolution étranges. Détecter des **écarts entre intuition, prix, règles de résolution et liquidité**, sans prétendre qu'un prix faible offre un gain assuré.

## Deux modes à ne pas confondre
1. **Exploration / divertissement** : classement des marchés improbables par originalité, humour, probabilité affichée et règles de résolution.
2. **Analyse quantitative / recherche** : estimation externe incertaine, scénarios, spread, profondeur d'ordre, frais, durée de blocage du capital, risque de contestation et conditions exactes de résolution.

Le simple fait qu'un événement semble « impossible » ne garantit pas que la position inverse est achetable au bon prix ou rentable après les coûts.

## Flux de données / architecture envisagés
- Collecte **lecture seule** via API publique officiellement permise, respect quotas et conditions.
- Normalisation `market_id`, libellé, catégories, échéance, issues, probabilité implicite, règles et oracle/source de résolution, carnet et volumes lorsque disponibles.
- Pipeline : filtres de qualité → signaux d'« étrangeté » → contrôle des clauses ambigües → simulation de gain/perte **théorique** → classement explicable.
- IA facultative pour repérer ambiguïtés, contradictions de wording et vérifier la définition du résultat ; sorties accompagnées de citations, niveaux de confiance et refus de conclure sans preuve.
- Cache et base historisée pour éviter le biais rétrospectif ; horodatage de chaque prix observé.

## MVP
Lire des données publiques sans compte de trading, afficher dix marchés insolites avec leur **texte de résolution en évidence** ; créer une liste d'observation et une simulation papier. Aucun ordre, clé de portefeuille, dépôt, contournement territorial ni promesse d'arbitrage.

## Recherche à mener
Comparer prix `YES/NO` réels, spread, carnet et frais ; construire un corpus d'issues passées avec résultat officiel connu pour tester la calibration ; mesurer faux positifs du détecteur de « certitude » et l'impact de la liquidité. La valorisation de contrats ne se réduit pas à la probabilité que suggère le titre du marché.

## Limites juridiques / éthiques
En plus des restrictions du site, vérifier les règles nationales et l'accès aux **données** avant toute collecte. Ne pas mettre en place d'accès par procuration pour contourner une géorestriction. Les marchés sur décès, catastrophes ou désinformation doivent pouvoir être masqués.

## Questions ouvertes
Curiosités humoristiques uniquement, ou étude académique de mauvaises valorisations ? Source unique Polymarket ou comparaison avec d'autres marchés accessibles ? Alertes et tableau de bord historique ou simple sélection quotidienne ?
