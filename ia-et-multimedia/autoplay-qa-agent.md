# AUTOPLAY — Agent IA de test autonome de jeux vidéo

**Statut : idée logicielle/IA non démarrée.** Retenue explicitement le 31 octobre 2026. Aucun agent connecté à un jeu ni campagne de tests exécutée. **Dépôt autonome envisagé :** autoplay-qa-agent.

## Proposition
Créer un **joueur-testeur IA réutilisable** capable d'explorer un jeu, de comprendre progressivement ses règles, de rechercher des anomalies et de fournir aux développeurs **des preuves reproductibles** plutôt que des impressions générales.

La valeur n'est pas simplement « l'IA joue à un jeu ». Elle est de réduire le travail manuel de QA et d'équilibrage sans faire passer un joueur artificiel pour un test utilisateur humain.

## Fonctionnalités visées
- Brancher un jeu à un adaptateur d'observation/action : capture d'écran, touches, événements, horodatages et éventuellement état interne de debug clairement identifié.
- Exécuter plusieurs modes complémentaires : tests dirigés, exploration aléatoire structurée, puis agent fondé sur la vision et la planification.
- Définir des objectifs (atteindre l'arrivée, explorer la carte, survivre, gagner une partie, maximiser une stratégie) et des contraintes (nombre d'actions, durée, énergie, checkpoints).
- Détecter crashs, gels, boucles sans progression, zones inatteignables, comportements physiques incohérents et écarts entre attendu et observé.
- Enregistrer chaque session : version du jeu, seed quand disponible, paramètres, chronologie des actions, captures et résultat.
- Rejouer le scénario pour **confirmer la reproductibilité** avant de qualifier un problème de bug ; signaler les incidents non déterministes.
- Produire un rapport lisible : sévérité proposée, preuve, étapes de reproduction, limite du diagnostic, export GitHub Issue facultatif après revue humaine.

## Première application : Glitch Runner
Privilégier un adaptateur pour une **version contrôlée du jeu** plutôt qu'un pilotage générique de tout le bureau dès le départ.

**MVP P0-P2 :**
1. Lancer une version de test stable du jeu, transmettre des commandes, récupérer images et événements ; imposer un budget maximum par session.
2. Construire un baseline déterministe de scripts simples et d'exploration, avant d'ajouter un LLM : déplacements, sauts, collisions, trous, points de contrôle.
3. Produire 20 sessions rejouables, détecter au moins une situation problématique **si elle existe**, puis faire valider humainement le diagnostic. À défaut, publier le taux de couverture et les limites sans inventer de bug.

**Exemples de métriques :** pourcentage de niveau visité, distance maximale, temps sans progrès, actions par seconde, nombre d'impasses, proportion de scénarios rejoués à l'identique, coût et latence des décisions IA.

## Évolutions possibles
- Brancher Moonrail et les roguelites avec des adaptateurs différents : moteur tour par tour, règles explicites et traces de combats.
- Évaluer l'équilibrage de milliers de parties par simulations rapides **sans IA visuelle** lorsque le moteur le permet, puis demander à l'agent de rechercher les abus.
- Comparer des profils de joueurs simulés (débutant, prudent, agressif, optimisateur) et analyser où ils échouent.
- Préparer une PR de correction **uniquement sur validation** de l'équipe ; ne pas modifier automatiquement la production.

## Architecture candidate à challenger
Noyau de campagne + interface d'adaptateurs + stockage de traces + moteurs de stratégie + analyseur + interface web de rapports. Isoler l'exécution des jeux ; garder un mode sans modèle payant. Ne pas collecter de comptes utilisateurs, secrets ni données privées. Prévoir des limites CPU/GPU, des timeouts, et l'arrêt d'une partie bloquée.

## Points de vigilance
Une IA peut apprendre à exploiter un artefact de test, agir différemment d'un humain ou manquer un ressenti de jeu. Un succès de niveau ne démontre ni plaisir ni équilibre ; une vidéo seule ne prouve pas un bug. Respecter les licences des jeux, les systèmes anti-triche et les conditions d'utilisation. Priorité aux dépôts du propriétaire et aux environnements autorisés.

## Frontière avec l'existant
Glitch Runner et Moonrail sont **des jeux à tester**, non l'agent de QA. AUTOPLAY est indépendant du moteur et de l'univers de chaque jeu. Il ne remplace pas les tests unitaires, les tests automatisés déterministes ni les sessions de joueurs humains.

## Questions ouvertes
Premier adaptateur Godot natif ou navigateur ? Quel degré d'instrumentation est acceptable pour rester proche du jeu réel ? Vision via captures ou données structurées au MVP ? Quelles métriques d'équilibrage reflètent le mieux l'expérience des joueurs ?

**Passage à l'action :** créer le dépôt autonome avant la première implémentation et retirer cette idée de l'incubateur.
