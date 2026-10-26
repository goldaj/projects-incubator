# PO Forge — de l'idée au backlog exploitable

**Statut : idée non démarrée.** Cadrage enrichi le 2026-10-26. Aucun produit ni intégration n'est établi ici.

## Origine et problème
Idée proposée dans les échanges autour de petits outils utiles aux Product Owners. Le besoin probable est de **transformer une intention de produit peu structurée en éléments de travail compréhensibles et contrôlables**. Cette formulation est une interprétation de l'idée initiale, pas un cahier des charges validé.

Un PO reçoit un besoin du type « permettre à un assuré de consulter son dossier ». Entre cette phrase et un backlog que l'équipe peut estimer, il manque objectifs, utilisateurs, hypothèses, limites, découpages, règles métier et critères de validation.

## Cas d'usage concrets
1. Saisir le problème utilisateur, les parties prenantes, l'objectif et les contraintes.
2. Produire une carte de travail : opportunités, parcours, capacités, **epics**, **user stories**, règles métier et dépendances.
3. Générer des exemples de critères d'acceptation et de scénarios Given/When/Then, en montrant ce qui est **supposé** et ce qui reste à confirmer.
4. Relire le backlog selon des contrôles configurables : stories trop grosses, critères non testables, contradictions, valeur inconnue, dépendances oubliées.
5. Exporter un dossier Markdown/CSV/JSON, puis éventuellement vers Jira seulement avec accord explicite.

## Ce qui rendrait l'idée distincte
Des dépôts autonomes comme `user-story-studio` existent déjà : **PO Forge ne doit pas refaire un simple générateur de stories**. Sa proposition de valeur à tester serait le **cadrage de bout en bout, traçable depuis le problème jusqu'aux décisions et au backlog**, avec gestion de l'incertitude. S'il n'apporte pas ce surcroît mesurable, fusionner l'idée avec l'outil existant et la retirer de l'incubateur.

## MVP envisagé, pas décidé
- Formulaire ou texte libre avec exemple fictif, sans données clients.
- Graphe simple objectif → hypothèses → epic → stories → critères.
- Questions de clarification proposées plutôt que décisions inventées par une IA.
- Exports locaux et versions comparables ; aucune connexion obligatoire ni écriture automatique dans Jira.
- Mode sans IA possible pour templates et contrôles déterministes ; IA facultative, ses propositions restant à valider par un humain.

## Questions avant démarrage
Mesurer si l'outil réduit vraiment le temps de refinement **sans dégrader** la qualité. Définir une grille d'évaluation sur 5 briefs fictifs, la fidélité aux besoins d'origine, les hallucinations et les doublons avec les dépôts actifs. Choisir ensuite architecture et licence.

**Incertitude assumée :** aucun secteur métier, flux de travail complet ou niveau d'automatisation définitif n'a été approuvé. Ne pas utiliser cette fiche pour commencer à coder sans décision explicite.
