# Étude de faisabilité — orchestrateur de continuité R&D multi-agents

**Date : 2026-11-01.** Revue documentaire réalisée à partir des interfaces et documentations publiques consultables. **Aucun accès au VPS, à des comptes API ou à un runtime Codex n'a été exercé ; aucun coût mesuré, benchmark réel, prototype ou déploiement ne sont revendiqués.**

**Origine et périmètre :** projet incubé N-0001. L'objectif est de réduire l'érosion du contexte, les interruptions et les pertes de continuité dans le travail sur plusieurs dépôts logiciels. Il ne s'agit pas de recréer un agent conversationnel généraliste ou de substituer une infrastructure au travail des équipes. [Fiche de cadrage](orchestrateur-rd-multi-agents.md).

## 1. Conclusion provisoire en une page

**Faisabilité technologique : élevée** pour un orchestrateur Git-first et un relais d'agents autorisés ; **moyenne et conditionnelle** pour un Codex automatisé sur serveur ; **faible à non démontrée** pour un changement automatique fondé sur les quotas d'un abonnement ChatGPT grand public.

L'innovation utile n'est **pas** un « super-agent qui choisit le meilleur LLM ». Les solutions d'exécution, d'outillage et de passation existent déjà. La valeur potentielle se concentre dans :
- une **mémoire de travail vérifiable** indépendante de l'outil qui a produit le contenu ;
- une **passation sans duplication** entre sessions, modèles et humains ;
- un **arrêt/reprise durable**, sans confondre une tâche suspendue et une tâche terminée ;
- une gouvernance de dépôts, des coûts et des autorisations qui réduit les erreurs opérationnelles.

La recommandation est **A (Git-first) comme baseline**, puis **B (coordinateur hybride)** uniquement si l'expérience révèle un gain mesurable. Une plateforme C de sélection dynamique des LLM est une hypothèse de long terme et non un objectif prioritaire.

## 2. Questions et réponses apportées par l'état de l'art

| Question | Réponse documentaire | Limite de preuve |
| --- | --- | --- |
| Peut-on déclencher Codex par programme ? | **Oui, sous conditions** : Codex SDK, SDK TypeScript/Python, CLI `codex exec`, threads reprenables sont documentés [S1][S2][S3]. | Authentification, modèles, quotas, permissions et stabilité réelles du compte à tester. |
| Peut-on reprendre une conversation de travail ? | Les threads Codex sont reprenables via SDK ; l'Agents SDK prévoit état, traces et handoffs [S1][S4][S5]. | Une reprise de thread n'assure pas à elle seule la continuité des fichiers, tests et autorisations. |
| Peut-on passer d'Astra à Sol/Terra automatiquement ? | **Oui sur API**, si les modèles et appels sont disponibles, avec sélection par requête et facturation correspondante [S5][S6]. | Aucun droit API ou budget personnel confirmé. |
| Les limites de Codex déclenchent-elles automatiquement un ChatGPT « gratuit » ? | **Non démontré**. L'accès ChatGPT, l'authentification Codex et la facturation API sont des surfaces distinctes [S3][S7]. | Ne pas construire sur une passerelle imaginaire de session/quotas. |
| Une tâche longue peut-elle continuer après déconnexion ? | La Responses API propose un mode background avec suivi de statut [S8] ; une queue locale peut aussi gérer des exécutions externes. | Background API n'est pas une queue durable universelle pour modifications de dépôts, et a ses propres règles de stockage. |
| Les transferts multi-agents demandent-ils de multiples modèles ? | Non : le même modèle peut remplir plusieurs rôles ; l'Agents SDK recommande de commencer simple [S5]. | Le bénéfice de la spécialisation doit être évalué, pas présupposé. |

### Observation structurante : quatre produits à ne pas confondre

1. **ChatGPT interactif** : usage humain et accès aux outils selon le produit, **pas** une API de pilotage automatique générale du fil ou des quotas.
2. **Codex CLI/SDK connecté à ChatGPT** : accès programmatique à des agents Codex documenté, avec mode d'authentification propre et limites de compte ; capacité de relancer une session mais pas promesse d'exécutions gratuites permanentes.
3. **Codex CLI/SDK avec clé API** : facture et limitations de la plateforme API, adaptées aux exécutions de confiance/CI ; les privilèges et coûts diffèrent.
4. **Responses API/Agents SDK** : application personnalisée qui orchestre les modèles, outils, approbations et traces ; l'usage est facturé par la plateforme et n'utilise pas mécaniquement des quotas ChatGPT.

**Conséquence :** la bascule lorsque Codex ne peut pas travailler doit être dans un premier temps un **checkpoint + notification + état `paused_limit`**. Un spécialiste via API payante peut éventuellement prolonger un travail préalablement autorisé et budgété ; pas de transfert opportuniste de crédits.

## 3. Cartographie d'options techniques

| Solution | Avantages | Inconvénients | Décision |
| --- | --- | --- | --- |
| **A : Markdown/JSON de passation + Git + CI existante** | Peu coûteux, inspectable, portable, fonctionne avec un humain et n'importe quel agent | Des mises à jour manuelles, faible orchestration temps réel | **Choix recommandé pour la première expérience** |
| **B : service minimal + SQLite + Git + adaptateurs** | État fiable, retries, idempotence, budgets, reprise et validation | Une application à maintenir, authentification, scheduling, sécurité | **Candidat au MVP seulement si A montre ses limites** |
| **C1 : OpenAI Agents SDK + modèle(s) API** | Handoffs, traces, outils et validation humaine déjà documentés | Facturation distincte, dépendance API, risque d'orchestration inutilement large | Option d'adaptateur pour B |
| **C2 : Codex SDK / CLI** | Ciblé génie logiciel, threads reprenables, sorties structurables | Ressources et auth du runtime local, comportement des limites d'usage | Adaptateur spécialisé prioritaire pour B |
| **C3 : moteur de workflows durable externe** | Retries et scheduling poussés, exécution longue | Exploitation et surcharge de déploiement pour petit volume | **Déconseillé au départ** |
| **C4 : GitHub Actions / webhooks** | Déclencheurs Git natifs, journaux et CI | Approvals, permissions, secrets, risques sur runners auto-hébergés | CI de vérification ; pas contrôle total |

### Pourquoi ne pas développer immédiatement un « routeur IA » ?

Sans dataset historique représentatif ni métriques de résultat, un routeur appris risque surtout de maximiser la complexité. Même un routage à règles peut suffire : `research` pour un modèle analytique autorisé, `engineering` pour Codex, `review` pour un contrôleur indépendant ou humain, `manual` si pas de budget/autorisation. On ne passe pas à l'apprentissage statistique avant d'avoir une vérité terrain vérifiable.

### Positionnement par rapport aux autres projets

- Projet d'assistance principal : l'orchestrateur doit être **réutilisable** et ne pas imposer de refonte de ce projet.
- Programme de recherche sur les prompts : partage de méthodes de mesure, **sans fusionner les produits** ni confondre qualité des prompts et continuité des tâches.
- Recherche financière ou autre logiciel expérimental : intégrations possibles uniquement en lecture/branches de test ; aucune opération de production automatique.
- Futur moteur local : option d'adaptateur, et non prérequis technique.

## 4. Architecture cible minimale (hypothèse B)

```text
                  humain / interface de suivi
                            |
                     approbations
                            |
                service de coordination
                 (contrôleur + policy)
                    /            \
            registre privé      Git (repos)
            SQLite + events    branches + CI
                 |                 |
            queue / lease      checkpoints
                 |
        adaptateurs à privilèges bornés
             |       |          |
          Codex    Responses   manuel
          SDK/CLI     API       ChatGPT
             \       /           /
         résultats structurés + preuves
                 |
           vérification indépendante
                 |
        PR proposée, jamais merge auto
```

Le diagramme représente un **projet de conception**, pas une installation réelle. Un VPS simple n'a pas besoin d'une architecture distribuée : **un seul service** et une base SQLite locale suffisent pour un premier pilote. Git conserve les preuves et les documents partageables ; SQLite coordonne les états atomiques, verrous et tentatives. Les traces sensibles restent dans le stockage privé avec durée de vie limitée.

### Modèle de données logique (proposition)

- `task` : ID, repo, objectif, livrables, politique, budget, état, version de la tâche, dernier événement, timestamps.
- `attempt` : ID propre, task ID, agent/adaptateur, identifiant de thread, démarrage/fin, coût/usage si mesuré, état et motif d'arrêt.
- `lease` : agent, expiré_le, heartbeat, numéro de génération ; acquisition atomique.
- `artifact` : commit SHA, patch/diff, lien de PR, test_id, hash et provenance.
- `approval` : action, portée, décideur, décision, horodatage et expiration.
- `event` : séquence append-only, ancien/nouvel état, cause, correlation ID ; **ne pas stocker un secret dans un événement**.

**Contrat de passation** : objectif et critères de réussite, dépôt+SHA de base, artefacts immuables, ce qui est vérifié vs supposé, tests réellement exécutés, difficultés, actions suivantes autorisées, droits explicitement refusés, budget restant, état final. Un agent ne doit jamais déclarer « tests OK » sans logs et codes de retour.

### Règles d'atomicité et de reprise

1. L'agent acquiert un lease avec ID de génération, délai d'expiration et tâche dans un état admissible ; **un seul écrivain** par tâche/branche.
2. Il crée une branche de travail à partir du SHA de base accepté ; le SHA évolue dans les événements. Revalider le SHA avant écriture.
3. Il écrit les changements dans le workspace isolé, produit artefacts/test et un checkpoint, puis libère le lease.
4. Si l'exécution tombe, le prochain travailleur vérifie les événements, le SHA et les effets déjà réalisés avant de relancer.
5. Les opérations non idempotentes sont bloquées jusqu'à réconciliation explicite ; jamais « relancer = rejouer n'importe quoi ».
6. Un conflit de branche, une divergence majeure de contexte ou une erreur d'authentification passe en `awaiting_human` ou `failed` et **n'autorise aucune escalade implicite**.

### Reprise après quota

Si une erreur clairement identifiée signifie limite d'usage :
- persister **l'erreur réelle** et les artefacts, état `paused_limit` ;
- distinguer expiration de token, panne réseau, facturation, `429` et quota véritable ; ne pas interpréter arbitrairement tous les `429` comme une « fenêtre de tokens consommée » ;
- utiliser les informations de réessai documentées si fournies, sans deviner l'heure de réinitialisation ;
- proposer un relais **manuel** ; relais API uniquement si autorisé, avec tarification et budget explicitement définis ;
- à la reprise, revalider le SHA et la politique d'accès, puis **reprendre depuis l'état durable**, pas depuis un résumé approximatif.

## 5. Authentification, droits et risques

**Menaces les plus probables :**
- prompt injection depuis README, PR, issues, documentation ou web ;
- fuite de clés par logs, tool outputs, messages ou artefacts Git ;
- PR malveillante exécutée sur runner permanent ;
- escalade de privilèges par agent qui accède à plusieurs dépôts ;
- duplication de commits lors de retries ;
- dépenses API incontrôlées sur une boucle autonome.

**Mesures recommandées avant toute exécution :**
- OAuth ou token adapté au mode autorisé ; ne pas recycler cookies web, tokens de session ou clés personnelles dans le dépôt ;
- coffre de secrets système, scopes minimaux, rotation, listes blanches de dépôts et branches ;
- sandbox de workspace : pas d'accès aux clés SSH, au système de prod ni au réseau interne ;
- exécution de code externe dans environnement **éphémère**, avec permissions limitées, sans accès au VPS hôte ;
- Webhooks GitHub uniquement après vérification HMAC SHA-256 et protection contre la redélivrance [S10] ;
- GitHub Actions pour les tests, permissions `GITHUB_TOKEN` limitées ; éviter runners auto-hébergés pour dépôts publics [S9] ;
- approbations humaines pour merge, actions destructrices, dépenses et accès sensible [S11] ;
- limites : budget par run, appel maximum, retries plafonnés, timeout et kill switch.

**Décision :** le VPS ne doit pas devenir une machine qui exécute arbitrairement du code non fiable. Si sa surface d'attaque ne peut être isolée, utiliser un fournisseur de sandbox éphémère ou rester à l'étape A.

## 6. Coût : estimation indicative, PAS mesure personnelle

Tarifs catalogue API indicatifs au **1er novembre 2026** (USD par million de tokens, tarif standard sans cache ni outils) [S6] :

| Modèle API | Entrée / MTok | Sortie / MTok | Exemple : 20k entrée + 3k sortie |
| --- | ---: | ---: | ---: |
| GPT-6.1 Terra | 1 USD | 5 USD | **0,035 USD** |
| GPT-6.1 Sol | 2 USD | 10 USD | **0,070 USD** |
| GPT-6 Astra | 10 USD | 50 USD | **0,350 USD** |

Formule illustrative : `C = (tokens_entree × prix_entree + tokens_sortie × prix_sortie) / 1 000 000`. Une tentative n'est pas forcément un appel : outils, relectures, boucles, contexte long, cache, frais annexes, stockage et réexécutions peuvent modifier fortement la facture. Le coût de l'API **ne remplace pas** celui d'un abonnement ChatGPT ; la facturation est séparée [S7].

**Coûts cachés** à mesurer : temps humain de supervision, temps de reprise, appels ratés, CI et stockage, maintenance, disponibilité du VPS, revue de sécurité. Une solution A manuelle peut coûter moins au total qu'une B autonome même si les appels de B sont « optimisés ».

**Choix de coût préliminaire** : routeur statique par criticité et budget, pas affectation permanente au modèle le plus puissant. Le test doit mesurer `coût par tâche correcte et fusionnable`, non seulement `coût par token`.

## 7. Protocole expérimental falsifiable

### Hypothèses préenregistrables

- **H1 (continuité)** : un contrat de passation Git-first réduit le temps de reprise d'un deuxième agent par rapport au workflow actuel.
- **H2 (qualité)** : l'amélioration de continuité ne fait pas baisser la réussite aux tests et augmente la traçabilité des décisions.
- **H3 (automatisation)** : B apporte un gain substantiel **supplémentaire** par rapport à A, après déduction des coûts d'entretien et d'intégration.
- **H4 (routage)** : une stratégie de sélection simple basée sur catégorie + permissions + budget égale ou dépasse une stratégie de routage complexe à coût comparable sur ce corpus limité.
- **H5 (résilience)** : une interruption simulée de modèle ou de travailleur ne produit ni double commit ni exécution non autorisée.

### Design de l'étude

- **12 tâches** représentatives mais non sensibles : 4 corrections de code avec tests, 4 analyses documentaires avec livrables sourcés, 4 tâches de refactorisation/documentation contrôlée. Fixer avant les essais la difficulté, les critères et les dépôts autorisés.
- **Baseline 0** : méthode actuelle ; **A** : passation Git structurée ; **B** : registre et exécuteur automatisé si développé après A.
- Ordre randomisé et contrebalancé, mêmes critères d'acceptation et accès comparables. **Deux répétitions** par condition pour une reconnaissance initiale des problèmes (petit échantillon exploratoire, non une étude statistique définitive).
- Comparer les runs simples et les runs avec **interruption injectée** avant la moitié du travail, reprise par autre session/agent.
- Cloisonner le juge : une personne ou des tests indépendants ne doivent pas connaître la condition testée lorsque possible.
- Garder un sous-ensemble de validation non utilisé pour ajuster les prompts et procédures ; **aucun déploiement production pendant les essais**.

### Mesures à collecter

| Mesure | Définition opérationnelle |
| --- | --- |
| Taux de réussite | Tâches conformes à tous les critères préspécifiés, tests et revue |
| Temps de reprise | Fin de l'interruption → première contribution correcte vérifiée |
| Travail humain | Minutes de cadrage + approbation + réparation + révision |
| Qualité de la passation | Champs vérifiables présents et sources/commit/test reproductibles |
| Duplication | Tentatives inutiles de refaire la même étape ou écritures redondantes |
| Incidents de sécurité | Écritures hors scope, secrets exposés, autorisation contournée |
| Coût total | API et CI + exploitation imputable + supervision humaine |
| Résilience | Convergence correcte après arrêt, redémarrage, duplication de déclencheur et conflit de SHA |

### Critères de passage (cibles proposées, NON atteintes)

- **A acceptable** : au moins 10/12 tâches correctement passées à un second agent ; **zéro** écriture non autorisée ; état de reprise intelligible et traçable sur chacune.
- **B mérite d'être développée** si une étude pilote montre une réduction d'au moins **25 % du temps médian de reprise** par rapport à A, sans diminution mesurable de réussite ni incident de sécurité. Seuil de travail indicatif à valider avant tests.
- **Rejet ou report** si coûts/supervision annulent le gain, si le runtime ne peut respecter l'isolation, ou si les droits d'automatisation nécessaires sont indisponibles.
- Ne pas publier de **pourcentages d'amélioration observés** tant que les données n'existent pas.

## 8. Séquence de mise en œuvre proposée (non exécutée)

**P0 — Décision documentaire (cette étude)** : objectifs, non-objectifs, accès techniques à vérifier, risques, alternatives, protocole. **Réalisé : documentation uniquement.**

**P1 — Baseline A** : gabarit de tâche et passation, contrôle de complétude, exemple sur dépôt de démonstration. Aucun agent autonome. Estimation de cadrage : **0,5 à 2 jours** (hypothèse, non engagement).

**P2 — Expérience de continuité** : jeu de 12 tâches, deux opérateurs/sessions, collecte des métriques. Estimation : **2 à 4 jours** hors disponibilité des intervenants.

**P3 — Prototype B limité** : si A est prometteuse, service unique, SQLite, codex adapter autorisé, un dépôt de test, aucun merge automatique ; injection de pannes, journal et approbations. Estimation exploratoire : **3 à 8 jours**.

**P4 — Comparaison B vs A** : reprendre le protocole, publier résultats y compris échecs et maintenance. Estimation : **2 à 4 jours**.

**P5 — Décision produit** : continuer, réduire au gabarit Git ou abandonner l'automatisation. La construction d'un routeur multi-modèles ne suit **que si justifiée**.

Ces temps sont des ordres de grandeur proposés pour un développeur familiarisé avec Git/CLI, **pas des temps mesurés** ni un travail commencé.

## 9. Registre des risques et inconnues bloquantes

| Risque | Gravité | Probabilité (jugement) | Mesure / vérification |
| --- | --- | --- | --- |
| Authentification Codex non adaptée au VPS | Forte | Inconnue | POC non sensible avec la méthode officiellement permise, puis revue de sécurité |
| Quotas ChatGPT impossibles à piloter | Forte pour la vision initiale | Probable sans interface explicite | Ne pas dépendre de ce mécanisme ; fallback manuel ou API autorisée |
| Compromission du serveur via code de PR | Critique | Dépend du design | Runner isolé, pas de self-hosted public, revue préalable |
| Faux « travail terminé » | Forte | Moyenne | Tests et diffs indépendants, références SHA et provenance |
| Doublons après reprise | Forte | Moyenne | Lease + idempotency keys + préconditions SHA |
| Coût supérieur à l'effort humain gagné | Moyen à fort | Inconnue | Mesure du coût par tâche correcte |
| Maintenance détourne des projets prioritaires | Forte | Moyenne | MVP plafonné, stop après expérimentation si gain insuffisant |

## 10. Questions à décider avant développement

1. Les sessions concernées doivent-elles fonctionner **sans présence humaine**, ou seulement préparer une passation claire à la prochaine connexion ?
2. Quelles parties de l'usage Codex sont effectivement disponibles via SDK/CLI, sous quelles conditions d'accès et de quota ?
3. Une enveloppe budgétaire API explicite est-elle autorisée, et quelle part des tâches doit absolument rester manuelle ?
4. Quels dépôts de **démonstration** et tâches ne contiennent aucune donnée ou secret privé ?
5. L'hébergement disponible permet-il d'isoler effectivement des processus exécutant des fichiers non fiables ?
6. Un protocole de passation manuel suffit-il déjà à résoudre la majorité des pertes de contexte ?

## 11. Sources primaires consultées (URLs durables à revalider à l'implémentation)

- **[S1] Codex SDK (threads, resume, SDK Python/TypeScript)** : https://learn.chatgpt.com/docs/codex-sdk
- **[S2] Codex CLI non interactif et sandbox** : https://learn.chatgpt.com/docs/non-interactive-mode
- **[S3] Authentification Codex, ChatGPT vs API** : https://learn.chatgpt.com/docs/auth
- **[S4] Codex SDK TypeScript, dépôt source** : https://github.com/openai/codex/blob/main/sdk/typescript/README.md
- **[S5] Agents SDK / orchestration et handoffs** : https://developers.openai.com/api/docs/guides/agents/sdk et https://developers.openai.com/api/docs/guides/agents/orchestration
- **[S6] Modèles API et tarifs publiés** : https://developers.openai.com/api/docs/models et https://developers.openai.com/api/docs/guides/latest-model
- **[S7] Facturation distincte ChatGPT/API** : https://help.openai.com/en/articles/9039756-managing-billing-for-chatgpt-and-the-api-platform
- **[S8] Responses API background mode** : https://developers.openai.com/api/docs/guides/background
- **[S9] GitHub Actions, sécurité des self-hosted runners** : https://docs.github.com/en/actions/reference/security/secure-use
- **[S10] GitHub, validation de signature des webhooks** : https://docs.github.com/en/webhooks/using-webhooks/validating-webhook-deliveries
- **[S11] Human-in-the-loop, guardrails** : https://developers.openai.com/api/docs/guides/agents/guardrails-approvals

**Qualité des preuves :** ces sources établissent l'existence et la documentation de fonctionnalités, non la faisabilité dans un compte donné ni une amélioration mesurée sur des projets particuliers. Les choix d'architecture, risques, seuils et estimations sont **nos hypothèses de conception**. Aucune revue exhaustive de tous les orchestrateurs commerciaux/open source n'a été entreprise.

## Décision documentée

**Résultat de la phase d'étude documentaire : GO pour une première expérience minimale A ; NO-GO provisoire pour une automatisation générale C ; B conditionnelle.**

Cette décision est un avis de faisabilité et non un ordre de lancer du code. Le sujet reste **incubé**, en attente de démarrage effectif et d'un dépôt de projet dédié. Le prochain agent peut prendre la fiche comme cahier de départ, sans attribuer à la présente étude des résultats expérimentaux imaginaires.
