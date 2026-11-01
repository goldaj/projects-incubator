# Narrative Weave Lab — outillage d'histoires entrelacées pour Romance Multiverse

**Statut au 1er novembre 2026 : idée explicitement transférée de Notepad vers l'incubateur ; étude documentaire initiale effectuée, aucun développement démarré.**

**Objet :** créer ou assembler une **chaîne d'outils réutilisable** permettant de concevoir, tester et industrialiser des narrations interactives dans lesquelles les histoires divergent, se rencontrent, se mélangent, se séparent de nouveau et changent parfois de genre ou de gameplay, sans incohérence de personnages, de temps, de connaissances ou de causes.

- **Jeu bénéficiaire :** [Romance Multiverse](../jeux/romance-routes-collection.md), idée de jeu elle aussi **non commencée** ; l'outillage est un chantier distinct et réutilisable, dont les livrables seraient un schéma de récit, des validateurs, simulateurs, éditeurs, exporters et rapports.
- **Provenance :** note privée Notepad **B-0022** du 2026-11-01, suivie d'une demande explicite de transfert et d'étude dans la conversation « Avancement pour Codex ». **Le verbatim de la note privée n'est pas publié ici.**
- **Priorité du propriétaire :** **la difficulté centrale n'est pas nécessairement le volume de texte**. C'est la cohérence des **embranchements qui se recoupent et s'entremêlent**, l'intérêt de lecture et la vitesse de progression du pipeline de création.
- **Étude technique sourcée :** [Étude des outils, méthodes, architecture et chaîne industrielle](etude-recits-entrelaces-2026-11-01.md).
- **Exemple vérifiable sur papier :** [Scénario miniature de divergence/reconvergence et cas d'essai](exemple-reconvergence-recits-2026-11-01.md).
- **Nature de l'intervention actuelle :** cadrage et recherche à partir de documentations publiques ; aucune bibliothèque installée, aucun prototype exécuté et aucun moteur choisi définitivement.

## Proposition de valeur

Un auteur ou une équipe peut définir une histoire commune, plusieurs fils d'intrigue, des épisodes spécifiques, des événements conditionnels et de vrais carrefours ; les outils génèrent une **carte lisible**, indiquent quels événements sont possibles depuis quels passés et fournissent des **contre-exemples** lorsqu'une scène est contradictoire.

L'atelier doit répondre à des questions concrètes :

1. Deux joueurs arrivent au même bal ; l'un a sauvé A, l'autre l'a trahie. **Que sait A ? Quel dialogue et quel geste sont plausibles pour chacun ?**
2. Une enquête et une romance croisent une intrigue horrifique ; **un secret révélé dans une route peut-il apparaître dans une scène commune sans spoiler les autres ?**
3. Une scène est réutilisée à trois endroits ; **les horaires, lieux, relations et objets sont-ils encore cohérents ?**
4. Une nouvelle option est ajoutée ; **quelles scènes et fins peuvent changer ? Quelles routes deviennent inaccessibles ?**
5. Comment publier un épisode rapidement **sans relire manuellement tous les parcours possibles** ?

## Hypothèse de conception privilégiée (à comparer)

Un **modèle hybride : graphe dirigé + fils d'intrigue / storylets + état narratif explicite + scènes de jonction conditionnelles**.

- **Graphe :** arcs de progression obligatoires, choix, boucles volontaires, carrefours et fins ; une scène peut être atteinte depuis différentes routes.
- **État :** vérité du monde, connaissances par personnage, relations, temps, lieux, objets, faits révélés et événements irréversibles.
- **Storylets :** petites scènes admissibles lorsque leurs préconditions sont vraies et utiles selon un objectif dramatique, plutôt qu'un gigantesque arbre entièrement figé.
- **Jonctions :** même **lieu ou événement** n'implique pas nécessairement exactement le même dialogue ; les variantes légères restent liées à un tronc de scène commun et les incompatibilités bloquent l'entrée.
- **Orchestration :** chaque fil conserve ses tensions, promesses, révélations et échéances ; une scène commune peut faire progresser plusieurs fils simultanément.
- **Qualité :** simulation et contraintes assurent la logique ; revues éditoriales et playtests restent indispensables pour mesurer l'émotion et le plaisir de lecture.

Cette approche reste une **hypothèse**, pas une garantie que toutes les histoires générées seront intéressantes.

## Livrables envisagés pour une V1 de production des outils

1. Spécification versionnée des scènes, fils, états, relations, contraintes, choix, jonctions et variantes.
2. Validateur syntaxique/sémantique avec messages d'erreur reliés aux scènes et aux variables.
3. Graphe navigable par fil, acte, ambiance, personnage, événement et jonctions.
4. Simulateur de parcours déterministe avec graine, journaux d'événements et reproduction d'un bug.
5. Contrôles de portée : destinations inexistantes, fins inatteignables (dans les limites du solveur), sorties bloquées, préconditions non satisfaites et causalité temporelle.
6. Console de **replay des parcours** avec comparaison de deux histoires menant à un même carrefour.
7. Export et aperçu jouable vers **un moteur narratif choisi après benchmark** (candidats : ink/inkjs, Yarn Spinner + Godot, Ren'Py, Twine/Twee).
8. Rapports CI (régressions, couverture explorée, variantes, différences) et documentation pour Codex/auteurs.

**Exclusions V1 :** génération automatique illimitée d'histoires de qualité, production d'illustrations, plateforme cloud multi-utilisateur, preuve formelle exhaustive sur tous les états possibles, portages simultanés vers tous les moteurs.

## Priorités de recherche (ordre indicatif)

| Niveau | Chantier d'outillage | Critère de sortie |
| --- | --- | --- |
| P0 | Modèle de faits / connaissances / relations / temps | Une même jonction peut distinguer deux passés incompatibles |
| P0 | Conditions d'accès et effets typés des scènes | Pas de scène exécutée avec ses préconditions fausses |
| P0 | Validateur de graphes et vérification de parcours | Trace précise d'un softlock ou d'une contradiction reproductible |
| P0 | Scénario comparatif et banc de test des moteurs | Comparaison factuelle des solutions sur le même cas |
| P1 | Vue par fils narratifs et carte des intersections | Suivre les arcs sans afficher un graphe illisible |
| P1 | Playtest automatique et couverture | Échantillons documentés, limites d'exhaustivité visibles |
| P1 | Templates de scènes et industrialisation de contenu | Ajouter une variante sans recopier tous les arcs |
| P1 | Contrôle du rythme, révélations et promesses | Alertes à valider éditorialement, jamais « qualité garantie » |
| P2 | Assistants IA de proposition / contrôle, avec citations de l'état | Suggestion soumise à validation, diff vérifiable |
| P2 | Localisation, voix, assets, personnalisation des ambiances | Pipeline d'intégration versionné |

## Hypothèses et risques majeurs

- **Fausse reconvergence** : deux routes se recollent en oubliant ce que les personnages ont vécu. **Mesure :** comparer les états entrants et imposer des variantes, des conditions ou une vraie transformation de l'état.
- **Explosion de l'espace d'états** : les permutations de connaissance, amitié, objets et temps dépassent vite le nombre de scènes. **Mesure :** abstraction d'états, partitions significatives, recherche bornée, invariants et solveur ciblé.
- **Perte de singularité** : trop de scènes communes = choix cosmétiques. **Mesure :** conséquences durables, souvenirs évoqués, arcs exclusifs, variations du gameplay et reconnaissance explicite des choix passés.
- **Branche sans intérêt** : un algorithme peut confirmer qu'une route existe, mais pas qu'elle est émouvante. **Mesure :** playtests à l'aveugle, critères éditoriaux et collecte de retours.
- **Dépendance à un SaaS** : exports insuffisants, tarification, verrouillage. **Mesure :** Git comme source de vérité et format de données exportable.
- **Fausse estimation de faisabilité** : industrialiser la vérification est réaliste, mais le **jeu monstrueusement grand** n'est pas un livrable V1 garanti.

## Critères de décision avant démarrage

Une étude outillée ultérieure, dans un dépôt dédié si le projet est lancé, devra comparer au moins **deux** chaînes de production, sur un cas **identique** (voir scénario miniature) :

- **A :** ink + inkjs / Inky et vérificateur indépendant ;
- **B :** Yarn Spinner + Godot, avec storylets et vue des nœuds ;
- **C optionnelle :** Ren'Py + format de données et lint/tests du moteur.

Mesurer : temps pour coder le même scénario, facilité de fusion/séparation des fils, nombre de défauts détectés, effort d'ajout d'une branche, export jouable, dépendances/licences, facilité de test automatique et qualité du rendu. Fixer les métriques *avant* l'expérimentation pour éviter de sélectionner le gagnant à l'intuition.

### Passage au développement

À la décision explicite de lancement, créer un dépôt d'outillage autonome, y transférer cette fiche et les deux dossiers, documenter le protocole et construire les premiers composants. **Retirer alors** cette fiche de l'incubateur : l'étude documentaire actuelle ne lance pas à elle seule un produit logiciel.

**Ne pas confondre avec** [MANGA DIRECTOR](https://github.com/goldaj/Notepad) (composition graphique de manga), [AUTOPLAY](../ia-et-multimedia/autoplay-qa-agent.md) (agent générique de QA de jeu) ou [Romance Multiverse](../jeux/romance-routes-collection.md) (jeu final). L'atelier intervient au niveau **structure / logique / causalité / industrialisation du récit**.
