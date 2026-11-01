# Étude initiale — moteurs et industrialisation des histoires entrelacées

**Date :** 2026-11-01. **Niveau de preuve :** recherche documentaire sur sources officielles et dépôts publics consultés, plus propositions d'architecture **à tester**. **Aucun code testé localement, aucun benchmark mené**. Les liens et versions devront être revérifiés au lancement.

## 1. Reformulation du véritable problème

Le projet n'est pas seulement un visual novel avec beaucoup de textes et de boutons. C'est une **architecture narrative entrelacée** :

- Des épisodes peuvent produire plusieurs histoires autonomes dans le même monde.
- Des protagonistes, lieux, objets et événements sont partagés, mais leur sens change selon le passé du joueur.
- Les fils divergent et convergent ; **une convergence peut rouvrir plusieurs nouvelles divergences**.
- L'ambiance (romance, thriller, humour, horreur, polar, méta) et **parfois les mécaniques du jeu** dépendent des décisions.
- Des événements communs peuvent avoir lieu malgré des états du monde incompatibles ; la scène doit alors se **reconfigurer explicitement**, sans effacement des conséquences.
- Une mise à jour de chapitre doit être produite et vérifiée sans rejouer à la main l'intégralité des combinaisons.

**Trois questions d'ingénierie sont distinctes :** (A) peut-on parvenir à ce nœud ? (B) ce qui s'y déroule est-il causalement cohérent ? (C) est-ce intéressant et intelligible pour le lecteur ? A et une partie de B sont automatisables ; C nécessite des critères éditoriaux et des personnes.

## 2. Recensement des solutions existantes

Les fonctionnalités et contraintes ci-dessous sont **d'après les documentations** ; elles ne signifient pas que les solutions ont été installées, vérifiées ou intégrées dans notre environnement.

| Outil / classe | Faits vérifiés | Apport | Lacune pour notre usage | Décision provisoire |
| --- | --- | --- | --- | --- |
| **ink / Inky / inklecate** (inkle ; MIT) | Knots, stitches, diverts, gathers/rejonctions, variables, logique, tunnels, threads ; compilation CLI ; Inky éditeur | Très bon texte source versionnable et **branches qui se rejoignent** ; compilation et exécution sans usine à gaz | Pas de validation sémantique inter-fils/chronologie comme contrat natif ; storylets orchestrés à ajouter | **Candidat A prioritaire** |
| **inkjs** (MIT) | Runtime JavaScript et compilateur, utilisable Node/navigateur | Aperçu web jouable, simulation et tests Node si compatibilité de version assurée | Version du format JSON et compatibilité à figer avec ink source | Couple naturel avec ink |
| **Yarn Spinner** | Scripts, choix, variables, sauts/detours, graph view VS Code ; **node groups / storylets et saliency** ; intégrations Unity/Godot/Unreal selon versions | **Très bon candidat pour scènes dynamiques et fils entrelacés**, sélection contextuelle documentée | Sémantique de monde et causalité toujours à modéliser ; coût/licence/versions des intégrations à valider | **Candidat B prioritaire** |
| **Ren'Py** | Moteur de visual novel, menus, labels, conditions, rollback, traductions, **lint et automated tests** | Idéal si jeu principalement illustré, dialogues et distributions desktop ; tests de présentation documentés | Synchronisation des fils et validations relationnelles à développer séparément | Candidat de production fort, benchmark C |
| **Twine 2 / Twee 3 + Tweego** | Passages et éditeur de graphe ; plusieurs story formats ; compilation CLI via Tweego | Maquettes navigables et export HTML ; très pratique pour discuter d'un embranchement | Un immense réseau conditionnel reste complexe à maintenir ; JS/macros selon story format | Comparateur léger / prévisualisation |
| **articy:draft** | Édition de flows et objets ; export JSON/XML/Excel, Unity/Unreal et règles d'export | Graphes éditoriaux élaborés, structuration du monde, collaboration selon offre | Solution propriétaire ; **licence, coût, automatisation et export réel à valider** | À évaluer si l'éditeur devient critique |
| **Arcweave** | Éditeur visuel, composants réutilisables, test de récit, exports/intégrations annoncés | Prototypage et vue sur les relations | SaaS/dépendance à la plateforme ; modalités et limitations d'export par offre à tester | Option d'édition, pas source de vérité par défaut |
| **Godot Dialogue Manager** (MIT) | Dialogue non linéaire pour Godot 4.x, conditions/mutations, exemples visual novel ; runtime stateless | Alternative directe aux Yarn scripts dans Godot | Pas de modèle de cohérence narrative globale fourni | Alternative B2 |
| **ChoiceScript** | Inclut `quicktest` et `randomtest`, simulations multiples et couverture | **Référence méthodologique** pour QA automatique d'embranchements | Licence propre restrictive sur les usages commerciaux ; ne pas réutiliser sans examen | Étudier les idées de tests, pas adopter par défaut |
| **NetworkX** | Composantes fortement connexes, dominators, graphes orientés, parcours | Lint graphes, nœuds morts, cycles, goulots, points de jonction | Ignore l'état narratif si on lui donne seulement des arêtes | Brique du validateur |
| **Z3 SMT** | Solveur de contraintes sur types, entiers, booléens et expressions (API Python notamment) | Satisfiabilité de conditions, combinaisons d'états et témoins de contradiction | Modélisation nécessaire ; explosion / bornes et faux positifs selon abstraction | Piste P1 ciblée |
| **Git + CI + formats textuels** | Diff, revue, versionnement, tests automatiques | Industrialisation, responsabilisation et reproduction des parcours | Ne conçoit aucune intrigue à lui seul | Fondations recommandées |

### Références consultées, avec usage exact

1. ink — [guide de syntaxe, rejonctions et threads](https://github.com/inkle/ink/blob/master/Documentation/WritingWithInk.md), [README officiel et compilation](https://github.com/inkle/ink), [Inky et licence MIT](https://github.com/inkle/inky).
2. inkjs — [runtime, compilateur et compatibilités](https://github.com/y-lohse/inkjs).
3. Yarn Spinner — [documentation](https://yarnspinner.dev/docs/), [storylets et saliency](https://yarnspinner.dev/docs/yarn/03-advanced/02-storylets-and-saliency-a-primer/), [node groups](https://yarnspinner.dev/docs/yarn/03-advanced/01-node-groups/) ; documentations nouvelles indiquant une intégration Godot GDScript et un **Story Solver encore annoncé « Coming Soon »** : ne pas compter dessus comme fonctionnalité livrée.
4. Ren'Py — [documentation moteur](https://www.renpy.org/doc/html/), [lint](https://www.renpy.org/doc/html/developer_tools.html) et [tests automatisés](https://www.renpy.org/doc/html/testcases.html).
5. Twine — [story formats officiels](https://twinery.org/cookbook/starting/twine2/storyformat.html) ; Tweego — [compilateur CLI](https://github.com/tmedwards/tweego).
6. articy:draft — [exports et importations](https://www.articy.com/en/articydraft/feature-list/), [export JSON](https://www.articy.com/help/adx/Exports_JSON.html) ; Arcweave — [fonctions annoncées](https://arcweave.com/features).
7. Godot Dialogue Manager — [README](https://github.com/nathanhoad/godot_dialogue_manager), [gestion externe de l'état](https://github.com/nathanhoad/godot_dialogue_manager/blob/main/docs/State.md).
8. ChoiceScript — [dépôt avec quicktest/randomtest et licence](https://github.com/dfabulich/choicescript).
9. NetworkX — [strongly connected components](https://networkx.org/documentation/stable/reference/algorithms/generated/networkx.algorithms.components.strongly_connected_components.html), [domination et jonctions](https://networkx.org/documentation/stable/reference/algorithms/dominance.html) ; [Z3](https://z3prover.github.io/api/html/).

**Attention :** l'état des abonnements, licences des connecteurs, versions exactes de plugins et compatibilités jeu/éditeur sera figé au moment du benchmark ; un site annonçant une fonction ne prouve pas sa qualité dans notre projet.

## 3. Architecture narrative de référence — hypothèse

### 3.1 Séparer les entités

Le schéma devrait distinguer :

- **SceneDefinition** : ID stable, texte + slots de variantes, tags de genre, actes, lieu, durée, participants, budget d'attention.
- **Beat** : unité de tension/révélation/récompense au sein d'une scène ; peut progresser plusieurs fils.
- **PlotThread** : romance avec A, enquête, polar, horreur, méta ; objectifs, promesses, jalons, seuils de révélation.
- **Choice** : option visible, préconditions, effets et conséquence future voulue ; options indisponibles expliquées.
- **WorldFact** : vérité du monde (par exemple `letter_destroyed`, `alarm_triggered`) ; séparer `unknown` de `false`.
- **CharacterKnowledge** : `knows(character,fact)`, source, date de découverte, fiabilité éventuelle. La vérité peut exister sans être connue.
- **RelationState** : confiance, dette, rivalité, secret partagé, consentement ; bornes et évolution.
- **Event** : action irréversible horodatée, auteur, cible, préconditions, effets ; journal append-only et projection d'état courant.
- **WorldClock** : temps logique, ordre des événements et occupation des lieux/personnages.
- **JoinContract** : préconditions minimales, conflits admissibles, variantes obligatoires, faits normalisés, information qui doit survivre à la jonction.
- **Ending / Collection** : conditions et indices, portées de spoiler, progression inter-runs séparée de l'état d'une partie.

Une variable `route = horror` **ne suffit pas** : une scène peut être à la fois romantique et horrifique, tandis que certains personnages ignorent encore la menace.

### 3.2 Reconvergence sans amnésie

Définir une réunion par le même **événement pivot**, pas nécessairement par une ligne de texte identique. Exemple : le bal de l'école ou une panne électrique rassemblent les personnages, quelle que soit la route d'entrée.

Pour chaque jonction, vérifier :

1. **Admissibilité :** tous les états entrants satisfont les invariants nécessaires (lieu, personne présente, événement antérieur, temporel).
2. **Conservation :** les faits de l'histoire, blessures, promesses, trahisons, connaissances ne sont pas effacés.
3. **Reconnaissance :** au moins un passage ou geste obligatoire réagit aux divergences importantes pour le personnage.
4. **Poursuite :** la scène commune crée de nouveaux choix utilisables par toutes les classes d'états autorisées, sauf exclusion volontaire annoncée.
5. **Coût dramaturgique :** ne pas unir les arcs si cela détruit leur identité ; autoriser un **carrefour logique partagé à variantes** ou des rencontres seulement partielles.
6. **Impact durable :** les choix passés peuvent transformer l'accès à une fin ou le comportement futur, même après plusieurs troncs communs.

Une jonction **ne fusionne pas les états**. Elle peut les regrouper pour le rendu et le parcours. Le bon modèle de nœud de simulation est souvent `(scene_id, abstract_state)`, pas uniquement `scene_id`.

### 3.3 Fils narratifs, causalité et temps

- Chaque fil a un **état d'avancement** propre, des obligations et des promesses à payer : indice annoncé, personnage absent, conflit non résolu.
- Les événements possèdent un ordre causal partiel. Une scène peut demander deux prérequis provenant de **fils différents**.
- L'horloge du monde (créneaux) et la disponibilité de chaque personnage empêchent les doubles présences, sauf si une règle du récit les justifie.
- Une révélation est **indexée par témoin**, pas seulement par `secret_revealed = true`.
- Les scènes communes sont des occasions de **croisements de fils** (un même dialogue romance + enquête), et pas uniquement des points de compression du graphe.
- Le genre est modélisé comme un **vecteur de tonalités** (tendresse, menace, absurde, tension...), pouvant évoluer, plutôt qu'une étiquette exclusive constante.
- Prévoir des **transitions de tonalité** (scène tampon, motif partagé, escalade) pour éviter que l'histoire saute sans raison de la comédie à l'horreur.

### 3.4 Choix et intérêt de lecture

Classer les choix selon la conséquence principale : information, relation, coût, trajectoire, identité du narrateur, genre, gameplay, accès futur. Chaque choix majeur doit modifier au moins une de ces dimensions **observables ou payées plus tard**.

Fixer une politique d'**obligations de payoff** : une promesse créée à la scène S exige une scène de réponse accessible plus loin dans les routes pertinentes, ou une résolution explicite de son échec. L'outil peut alerter sur les promesses orphelines, pas décider si leur écriture est satisfaisante.

Pour limiter l'impression d'illusion du choix : mesurer les choix sans effets persistants, la distance jusqu'au prochain rappel de conséquence, la proportion de contenu spécifique à chaque classe d'états, et le taux de scènes où deux historiques donnent exactement le même texte malgré des faits importants différents. Ce sont des **proxies**, pas des juges de qualité littéraire.

## 4. Inventaire des outils à produire ou assembler (pistes hiérarchisées)

| ID | Module proposé | Concret et utile | Existant à exploiter | Priorité |
| --- | --- | --- | --- | --- |
| T01 | Catalogue de scènes et identifiants | Aucun lien cassé lors d'un renommage | Git, JSON Schema | P0 |
| T02 | Modèle de faits/relations/connaissances | Pas de « personnage omniscient » accidentel | Types, schéma de données | P0 |
| T03 | Contrats pré/postconditions | Autoriser ou refuser une scène depuis un état | DSL + validations | P0 |
| T04 | Éditeur de graphe multi-couches | Afficher scènes, fils, personnages, genres séparément | Inky/Yarn graph, React Flow éventuel | P1 |
| T05 | Reconvergence Inspector | Comparer **deux historiques** menant au même nœud | Diff d'état + replay | **P0** |
| T06 | Linter de structure | Orphelins, renvois morts, sorties introuvables, cycles non voulus | NetworkX | P0 |
| T07 | Testeur des états | Invariants sur faits et relations, contre-exemples | Hypothesis / Z3 à évaluer | P0–P1 |
| T08 | Simulateur de runs | Parcours enregistrés avec graine et étapes | Runtime natif du moteur | P0 |
| T09 | Explorateur de couvertures | Scènes/choix/conditions/fins non couverts | Tests à la ChoiceScript | P1 |
| T10 | Évaluateur de causalité/chronologie | Événements non ordonnés, lieux/horaires incompatibles | Contraintes, agenda logique | P1 |
| T11 | Gestion des promesses et payoffs | Indice ou secret oublié / récompense disproportionnée | Matrice des obligations | P1 |
| T12 | Bibliothèque de storylets | Réutiliser scènes contextuelles sans copier | Yarn node groups/saliency | P1 |
| T13 | Planificateur de scènes croisées | Trouver des intersections narratives plausibles | Contrats + graphe ; assistance IA facultative | P2 |
| T14 | Système de tonalité et transition | Éviter rupture brutale d'ambiance non motivée | Tags, règles, revue humaine | P1 |
| T15 | Variantes de rendu / répliques | Rappeler passés distincts dans une scène pivot | Conditions, templates, moteur | P0 |
| T16 | Compareur de runs en parallèle | Vérifier qu'une divergence a une conséquence | Journal événements, diff | P1 |
| T17 | Analyseur d'impact | Quelles scènes changent si une variable est renommée ? | Index des références, graphe | P1 |
| T18 | Générateur de rapports QA | CI avec preuves de bugs et sauvegardes reproductibles | GitHub Actions | P1 |
| T19 | Exporteur vers le moteur de jeu | Source unique / preview jouable | inkjs/Yarn/Ren'Py | P0 |
| T20 | Bibliothèque de templates éditoriaux | Accélérer les scènes à embranchements typés | Fichiers déclaratifs, snippets | P1 |
| T21 | Tableau de pipeline de production | Idée → contrat → rédaction → QA → illustration → intégration | GitHub issues/PR | P1 |
| T22 | Système de secrets et révélations | Ne pas spoiler une route depuis une autre | `knows(person,fact)` + portée | P0 |
| T23 | Storyboard de gameplay par route | Les branches peuvent changer le **genre de jeu** | Contrat de scène + `mode` | P2 |
| T24 | Export de localisation et lignes voix | IDs stables et traductions sans casser le graphe | Capacités moteur / outils de traduction | P2 |
| T25 | Assistant de revue IA à contraintes | Repérer incohérences possibles, proposer variantes | LLM avec sources du dossier, sans autopublication | P2 |
| T26 | Audit de répétitivité | Reconnaître scène copiée et passages trop semblables | Embeddings éventuels, contrôle humain | P2 |
| T27 | Pare-feu de la progression méta | Distinguer les connaissances du **joueur** et du **personnage** | Deux états et règles de spoilers | P1 |
| T28 | Visualisation des arcs et rythme | Tension, détente, révélations, climax par histoire | Tags + courbes tracées | P1 |
| T29 | Générateur de scénarios ciblés | Trouver automatiquement un parcours vers une scène précise | Recherche bornée / solveur | P1 |
| T30 | Analyse des économies de production | Temps et coût de créer/maintenir une route supplémentaire | Journal éditorial et métriques | P2 |

Les numéros identifient des **pistes**, pas 30 tickets à implémenter immédiatement. L'objectif est de choisir 5–8 outils qui réduisent réellement le coût des 20 suivants.

## 5. Stratégie de tests réaliste

### 5.1 Quatre couches

**L0, statique** : liens d'ID, variables non déclarées, conditions contradictoires simples, fautes de schéma, promesses sans débouchés. Une erreur = fichier/scène + motif et suggestion de correction.

**L1, graphe** : atteignabilité **structurelle** (ignore les états), fins orphelines, composantes fortement connexes, jonctions, dominators/post-dominators, boucles avec ou sans sortie connue.

**L2, états** : exploration symbolique ou BFS/DFS **bornée**, hachage d'états, scénarios dirigés, sampling seedé ; comparaison de deux historiques arrivant à une jonction. Conserver le **parcours témoin** des bugs. Une scène atteignable structurellement peut être impossible après évaluation des conditions.

**L3, éditorial et runtime** : playtests à l'aveugle, métriques de monotonie, cohérence perçue des personnages, compréhension des conséquences, plaisir de relire, éventuels changements de gameplay et tests du moteur réel.

### 5.2 Invariants prioritaires

- Aucun dialogue n'affirme la connaissance d'un secret sans source compatible (sauf personnage menteur, correctement balisé comme tel).
- Un personnage mort ou absent ne participe pas à une scène sans justification de route.
- Un objet détruit ne réapparaît pas sans événement de restauration.
- Une promesse narrative ne devient pas inaccessible sans conclusion ou indication délibérée.
- Les horaires sont compatibles avec les déplacements et actions.
- Une jonction n'écrase ni les relations ni l'identité d'un fil narratif.
- Une branche à gameplay différent ne déclenche pas une mécanique indisponible sur le moteur choisi.
- Chaque fin d'une famille revendiquée possède au moins un parcours témoin sous les hypothèses modélisées.
- Aucun lecteur ne voit un indice de collection qui divulgue la révélation d'une route non jouée si le mode anti-spoiler est actif.

### 5.3 Les limites à reconnaître

Prouver « toutes les fins atteignables » dépend du **domaine d'états** considéré, des bornes et du support des expressions. Les jeux à variables numériques libres, boucles et scripts arbitraires peuvent empêcher une preuve exhaustive pratique. Distinguer **preuve**, **résultat d'exploration bornée**, **échantillon de tests** et **intuition éditoriale** dans les rapports.

## 6. Chaîne industrielle proposée

```text
BIBLE DU MONDE (faits, personnages, règles, secrets)
     ↓
PLAN DE FILS (romance / polar / horreur / méta)
     ↓
CONTRATS DE SCÈNES (conditions, effets, payoffs, genre)
     ↓
ÉCRITURE MODULAIRE (tronc + variantes + storylets)
     ↓
COMPILATION / LINT / TESTS DE PARCOURS
     ↓
REVIEW DEUX ROUTES → MÊME JONCTION (diff des états)
     ↓
PR DE CONTENU + PREVIEW JOUABLE + RAPPORT QA
     ↓
PLAYTEST HUMAIN → RETOURS → CORRECTIONS
     ↓
EXPORT MOTEUR / INTÉGRATION AUDIO-VISUELLE / RELEASE
```

### 6.1 Organisation Git envisagée à la création du dépôt

- `world/` : faits, fiches personnages, lieux, lois et canon du monde.
- `threads/` : fils dramatiques et promesses/payoffs.
- `scenes/` : scènes modulaires et variantes.
- `joins/` : contrats de jonction, état entrant sortant.
- `rules/` : schémas JSON et invariants.
- `tests/` : parcours témoins, tests des règles, cas impossibles.
- `tools/` : parseur, linter, simulateur, couverture, exporteurs.
- `assets/` : références légères ; assets volumineux adaptés séparément.
- `reports/` : rapports générés **non** confondus avec preuves humaines.
- `docs/` : décisions, sources, guide auteurs, AGENTS et passation.
- `.github/workflows/` : CI de validation et prévisualisation.

### 6.2 Contrat d'une PR de scène

Une scène nouvelle devrait préciser : ID stable, place dans un ou plusieurs fils, **pré/postconditions**, événements modifiés, connaissance gagnée par chaque personnage, tonalité d'entrée/sortie, promesses posées/payées, variantes nécessaires selon les passés, dépendances visuelles, jeu/route(s) concerné(s), tests et parcours témoin.

Les validations sont rapides car les **tests d'impact** se concentrent sur les dépendants, mais un contrôle général périodique reste nécessaire (des dépendances dynamiques peuvent échapper à l'index statique).

### 6.3 Réduire l'effort sans écraser les choix

- Préférer des **diamants** avec événements communs et dialogues réellement différents à des arbres complets.
- Réutiliser une **scène pivot**, pas un bloc de texte aveugle au passé.
- Découper la narration en fils à état local et événements partagés explicites.
- Utiliser des **storylets conditionnels** pour les réactions courtes ; garder des séquences entièrement originales pour les changements de genre.
- Séparer mode de gameplay, habillage, texte, monde et progression inter-runs.
- Capturer un **cas témoin** dès la découverte d'un défaut : la prochaine modification doit conserver la correction.
- Limiter la génération IA à des propositions auditables, jamais à des changements de canon sans accord.

## 7. Programme de recherche comparative à exécuter APRÈS lancement

### Essai E01 — Deux routes, une jonction, deux états

Même bal, deux histoires contradictoires quant au niveau de confiance entre deux personnages. Produire deux dialogues différents à partir d'une scène centrale unique et conserver les effets après la scène.

**Échec :** une des entrées passe mais la scène ignore la trahison ou révèle un secret non connu.

### Essai E02 — Croisement simultané de trois fils

Une décision dans l'enquête provoque un effet sur la romance et sur l'ambiance horreur, sans interrompre l'enquête. Faire progresser plusieurs fils depuis un même événement.

**Échec :** des fils deviennent incohérents ou tous les chemins convergent sans conséquences durables.

### Essai E03 — Contradiction et contre-exemple

Créer volontairement un personnage présent à deux endroits incompatibles, un objet détruit réutilisé, un secret révélé hors de sa route et une scène sans issue. Le système doit afficher un **témoin reproductible** de chaque bug.

### Essai E04 — Changement d'ambiance et de gameplay

Une même bibliothèque devient lieu de romance, scène de crime ou environnement d'exploration horrifique selon le passé. Les modes doivent être compatibles avec les règles de navigation et de sauvegarde.

### Essai E05 — Industrialisation

Ajouter cinq scènes après coup, modifier une variable de relation, retirer un choix. Comparer outils sur **temps de changement, erreurs découvertes, taille du diff, effort QA et qualité du rendu**. Refaire l'expérience avec variantes et tester rollback.

### Table de décision de benchmark (à compléter réellement)

| Critère | Poids indicatif | ink + inkjs | Yarn + Godot | Ren'Py |
| --- | ---: | --- | --- | --- |
| Branches et reconvergences expressives | 20 % | À mesurer | À mesurer | À mesurer |
| Storylets / rencontres dynamiques | 15 % | À mesurer | À mesurer | À mesurer |
| Vérification et instrumentation | 25 % | À mesurer | À mesurer | À mesurer |
| Changement d'ambiance et gameplay | 15 % | À mesurer | À mesurer | À mesurer |
| Industrialisation, diff et CI | 15 % | À mesurer | À mesurer | À mesurer |
| Licence, indépendance, distribution | 10 % | À vérifier | À vérifier | À vérifier |

Les poids sont une **proposition de protocole**, pas le résultat d'une consultation utilisateur. Préenregistrer les poids finaux avant le test.

## 8. Décisions provisoires et suite

1. Ne **pas** développer un moteur narratif maison complet avant d'avoir testé les deux principaux moteurs existants.
2. Investir d'abord dans les **outils que les moteurs ne fournissent pas** : modèle de connaissances et contrats de jonction, comparaison d'historiques, simulateur de causalité, rapport de contre-exemples et qualité de l'industrialisation.
3. Préférer une source textuelle versionnable et des identifiants stables à une base d'éditeur propriétaire sans export fiable.
4. Organiser dès le départ une petite **bibliothèque d'histoires de test** et des exemples sciemment incohérents.
5. Réserver les interfaces très sophistiquées, agents IA et intégrations aux phases où leurs apports peuvent être mesurés.
6. **Critère humain fondamental :** une scène cohérente sur le plan logique mais ennuyeuse est un échec de conception. Les tests ne remplaceront pas la mise en scène.

**Statut réel : étude documentaire seulement.** Aucun essai E01–E05 n'a été effectué pendant la rédaction.
