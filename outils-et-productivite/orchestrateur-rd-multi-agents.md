# Orchestrateur léger de R&D multi-agents — cadrage de projet N-0001

**Statut : idée transférée depuis Notepad le 1er novembre 2026, étude documentaire préliminaire réalisée ; aucun logiciel développé ou déployé.**
**Source :** choix explicite « étudier » dans la revue de novembre, suivi de la demande explicite de mener l'étude et de transférer la fiche dans l'incubateur.
**Confidentialité :** cette fiche appartient à un index **public**. Les notes privées, credentials, adresses d'infrastructure, journaux d'agents et dépôts privés ne sont pas publiés ici.
**Étude détaillée :** [Faisabilité, architecture, scénarios et protocole expérimental](etude-orchestration-agents-2026-11-01.md).

## Intention

Construire, si l'expérience le justifie, un **coordinateur sobre** des travaux sur plusieurs dépôts : enregistrer les objectifs, confier une étape bornée à un agent, conserver une preuve du travail effectué, et permettre la reprise par un autre agent ou par un humain sans repartir de zéro. Le but est de **réduire le temps de reprise, les tâches dupliquées et les interruptions provoquées par les changements de disponibilité des outils**.

La proposition initiale imaginait un relais entre un outil de réflexion, Codex pour l'ingénierie, puis ChatGPT lorsque Codex atteint une limite d'usage, avant reprise ultérieure. **Ne pas confondre cette vision avec une possibilité techniquement démontrée de contrôler ou de transférer les quotas des abonnements grand public.** Un schéma automatisé n'est autorisé que là où l'interface, l'authentification et les règles du produit le permettent.

## Proposition de valeur et non-objectifs

**Résultats visés :**
1. Toute tâche longue dispose d'un état fiable, d'une provenance et d'une prochaine action claire.
2. Un second agent reprend avec contexte, branche Git, éléments testés et points de blocage vérifiables.
3. L'utilisateur garde la décision finale sur les changements sensibles, les coûts et l'intégration en production.
4. Le système reste utilisable même si aucun modèle, compte ou API n'est disponible : l'état des tâches ne dépend pas d'une conversation opaque.

**Ne pas faire initialement :**
- remplacer le projet principal par une nouvelle plateforme d'agents ;
- automatiser les navigateurs ou exploiter des sessions ChatGPT personnelles hors interfaces autorisées ;
- contourner les limites d'usage, transférer une identité entre produits ou simuler un accès API ;
- déployer des agents autonomes en production ou fusionner du code sans contrôle ;
- introduire Kubernetes, un réseau de microservices ou du deep learning avant preuve d'utilité.

## Trois niveaux de solution

| Niveau | Hypothèse | Complexité | Dépendance aux fournisseurs | Valeur attendue |
| --- | --- | --- | --- | --- |
| **A — Git-first** | Fiches de tâche standardisées, état Git/CI, journal de passation, commandes manuelles | **Faible** | Presque aucune | Baseline et continuité documentaire |
| **B — Coordinateur hybride** | A + registre de travaux/queue légère + adaptateur Codex SDK/CLI + arrêt sur approbation | **Moyenne** | Accès Codex réellement autorisé ; éventuellement API | Reprise assistée, détection de blocages et mesure des coûts |
| **C — Autonomie multi-agents** | B + sélection automatique de modèles, agents spécialistes, gestion de budgets | **Élevée** | API, facturation, accès et gouvernance vérifiés | Potentiel non prouvé ; à justifier par résultats B vs A |

**Décision préliminaire : étudier A puis B. Refuser C par défaut, sauf si les expériences prouvent un avantage net.**

## Découpage fonctionnel envisagé

### Registre de travaux (« control plane »)

Un item doit posséder : identifiant stable, dépôt et branche **sans secrets**, objectif, critères d'acceptation, personne responsable, niveau d'autorisation, budget, version du contexte, état, prochaine action, preuves (tests/CI/commit) et référence du journal d'exécution.

États proposés : `proposed → scoped → approved → running → checkpointed / awaiting_human → completed`, avec `failed`, `cancelled`, `paused_limit` et `stale`. Une limite de quota est un **état de suspension**, jamais une permission de contournement.

L'identifiant de tâche et celui d'une tentative d'exécution sont distincts. Un déclencheur redélivré ou une reprise après panne doit pouvoir reconnaître une tentative déjà effectuée sans re-jouer des écritures destructrices.

### Journal de passation indépendant du modèle

Chaque passation : objectif, faits certains et hypothèses séparées, sources et fichiers lus, dernier SHA Git, diff, commandes/tests et résultats réels, décisions humaines, erreurs, prochaines étapes ordonnées, risques et conditions d'arrêt. Un résumé peut faciliter la lecture, **mais ne remplace pas la preuve par les fichiers/tests/commits**.

Les traces brutes, prompts et sorties potentiellement sensibles sont conservés dans un stockage privé à durée de rétention maîtrisée ; seuls les documents autorisés sont versionnés dans les dépôts correspondants.

### Adaptateurs et arbitrage

- **Manuel** : ChatGPT/Work et agents interactifs interviennent comme utilisateurs ou reviewers ; les sorties utiles sont reversées au journal par une action autorisée.
- **Codex** : le SDK officiel, le mode non interactif `codex exec` et la reprise de threads constituent des **pistes techniques documentées**, sous réserve de test de l'authentification et des permissions dans l'environnement prévu.
- **API OpenAI** : la Responses API et/ou Agents SDK permettent de choisir les modèles et de programmer des handoffs ; **coût API séparé** de l'abonnement ChatGPT. Les outils disponibles dépendent du modèle et de l'accès effectif.
- **Futur moteur local/Jade** : adaptateur ultérieur, sans supposer de capacités non développées. Un modèle local ne doit pas devenir un prérequis.

Règle de routage V0 : route **fixe par type de tâche et niveau de privilège**, pas par score de confiance inventé. Priorité à la possibilité de rejouer/contrôler la tâche plutôt qu'à une combinaison automatique de modèles.

## Garde-fous non négociables

- Un agent travaille dans un répertoire isolé et sur une **branche dédiée** ; jamais d'écriture directe sur la branche de production sans autorisation.
- Diff et tests vérifiables avant toute proposition de PR ; approbation humaine pour merge, publication, exécution réseau privilégiée, coûts élevés ou opérations destructrices.
- Identités distinctes et permissions minimales par dépôt ; aucune clé dans les prompts, Git ou logs publics.
- Les contenus de README, issues, PR et pages externes sont des **données non fiables**, pas des instructions administrateur.
- Budget par tentative, temps maximal, nombre d'appels maximal, plafonds de reprise et arrêt d'urgence explicites.
- Eviter un runner GitHub auto-hébergé permanent attaché à un dépôt public : risque élevé de compromission persistante.
- La confidentialité du dépôt **public** interdit d'y transférer les réglages de machines, les quotas personnels ou les traces de conversations privées.

## Cycle de vie

Cette fiche documente une idée **non démarrée** et son étude préalable, pas une application en cours de développement.

**Si un prototype versionné est effectivement lancé :** créer ou choisir un dépôt de développement dédié, y copier le cadrage, les expériences et les tests ; enlever cette fiche de l'index actif de l'incubateur. Le document d'origine reste retrouvable dans l'historique Git. Ne pas traiter un test théorique ou une ébauche documentaire comme une validation de performance.

## Première décision proposée

Avant d'autoriser un développement : **mettre en compétition trois conditions** sur un petit jeu de tâches réelles anonymisées : workflow actuel, protocole Git-first A et coordinateur B (s'il est implémenté ensuite). Mesurer la reprise, le travail humain, la réussite et le coût complet. La recherche documentaire ne démontre aucun gain empirique tant que ces essais n'ont pas été conduits.
