# Decision Board — arbitrages explicables

**Statut : idée non démarrée.** Enrichissement documentaire 2026-10-26. L'ancien descriptif ne fixait que « comparateur multicritères pondéré ».

## Le problème
Une décision produit est souvent présentée comme évidente alors qu'elle dépend de **préférences discutables** : coût, impact, délai, risque, confiance dans les estimations. Decision Board est envisagé comme une **table de décision auditable**, pas comme une machine prétendant découvrir le « meilleur » choix.

## Scénario
Une équipe hésite entre « améliorer le parcours mobile », « refondre la recherche » et « réduire la dette technique ». Le PO définit cinq critères, leur sens, une échelle et les poids. Les participants renseignent les scores et leurs justificatifs. L'outil montre le classement **et surtout les conditions qui le feraient changer**.

## Fonctionnement conceptuel
- Créer des options, critères, unités et échelles (0–5, euros, jours, niveaux de risque).
- Déclarer pour chaque critère si **plus** est préférable ou si **moins** est préférable ; normaliser avec transparence.
- Séparer faits mesurés, estimations et opinions ; conserver provenance et niveau de confiance.
- Score pondéré expliqué ligne par ligne, comparaison par paires et analyse de sensibilité aux poids.
- Faire varier une hypothèse (« si le coût double ? »), identifier les ex æquo et les options dominées.
- Exporter résultat, hypothèses et raison de la décision ; conserver des scénarios sans falsifier l'historique.

## MVP à étudier
Une application locale et légère avec jeu de données fictif, trois à cinq options, matrice éditable, pondération, graphique de sensibilité et export Markdown/CSV. Les formules et leurs limites doivent être visibles. L'IA ne serait pas nécessaire.

## Frontière avec les projets existants
`backlog-prioritizer` traite déjà des méthodes de priorisation de backlog (RICE/WSJF). Decision Board n'est utile comme produit indépendant **que** si le besoin porte sur des **choix hétérogènes** et des controverses de critères, pas sur un nouveau tableau de priorisation identique. Valider cette distinction avant dépôt propre.

## Risques et prochaines recherches
L'agrégation peut produire une fausse précision ; des critères corrélés doublent artificiellement certains bénéfices et des poids arbitraires orientent la décision. Comparer pondération simple, modèles coût/bénéfice et « outranking » sur cas fictifs. Mesurer la compréhension des résultats par 2–3 décideurs avant de construire davantage.

**Non acté :** usage individuel ou atelier collectif, collaboration synchrone, source des scores et modèle de décision définitif.
