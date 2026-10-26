# Laboratoire de sociétés d'agents génératifs — Smallville 2.0

**Statut : idée scientifique non démarrée ; cadrage et protocoles proposés uniquement (aucun code ni test exécuté dans ce dépôt).**  
**Cadrage : 2026-10-26.**  
**Axes : agents autonomes, cognition/mémoire, simulation sociale, expérimentation scientifique, inférence locale.**

## Pourquoi ce projet ?

Reproduire d'abord l'expérience **Generative Agents / Smallville** (Park et al., Stanford/Google, 2023) : 25 personnages simulés, dotés d'une mémoire, de mécanismes de réflexion et d'un plan quotidien, produisent des interactions et une coordination sociale. Puis examiner ce qui devient possible avec les **LLM ouverts, les moteurs d'inférence et les méthodes scientifiques de 2026**.

Origine de l'idée : [vidéo « Ils ont enfermé 25 IA dans un village »](https://www.youtube.com/watch?v=jRBUHrusAyk). Elle rapproche Smallville, **Project Sid** (Minecraft, Altera) et des travaux sur des **jumeaux comportementaux** de personnes réelles : ce sont des expériences **différentes**, avec des protocoles et niveaux de reproductibilité distincts. La source primaire de ce projet reste l'article et le code Smallville.

**Objectif produit :** laboratoire reproductible (scénarios, protocole, simulateur, métriques, rejouabilité), avec visualisation 2D facultative. **Objectif scientifique :** mesurer sous quelles conditions des dynamiques collectives apparaissent, leur robustesse, leurs erreurs, et leur coût. Il ne s'agit ni de démontrer une conscience artificielle ni de prédire fiablement les êtres humains.

## 1. Questions scientifiques à trancher

| Hypothèse falsifiable | Variable testée | Mesure / contrôle |
|---|---|---|
| **H1 — mémoire** : mémoire épisodique et recherche améliorent les actions pertinentes. | Aucune mémoire / historique tronqué / mémoire récupérée. | Rappel factuel différé, objectifs accomplis, contradictions. |
| **H2 — réflexion** : synthétiser ses expériences améliore les plans, mais peut renforcer les faux souvenirs. | Réflexion absente / présente / avec vérification de provenance. | Cohérence des décisions et taux d'hallucinations transmises. |
| **H3 — taille du LLM** : un modèle plus gros n'améliore pas nécessairement la simulation à budget égal. | Familles et tailles de modèles, quantification et budget de tokens contrôlés. | Qualité sociale, faits respectés, latence, coût, variance. |
| **H4 — diversité sociale** : buts et profils hétérogènes changent coopération et conflits. | Agents homogènes / hétérogènes ; topologie du réseau ; force des liens. | Propagation des informations, coordination, conflits et résolution. |
| **H5 — contraintes du monde** : géographie, ressources et capacités physiques explicites réduisent les actions impossibles. | Monde « narré » vs moteur autoritaire et vérification des actions. | Taux d'actions rejetées, inventions de lieux/objets, erreurs. |
| **H6 — rareté** : une pénurie peut produire spécialisation, commerce ou compétition, sans que ces effets soient garantis. | Ressources abondantes / rares, règles identiques par ailleurs. | Tâches réalisées, échanges, pénuries, inégalités, coopération. |
| **H7 — agents hybrides** : déclencher le LLM seulement lors de décisions complexes diminue le coût sans trop dégrader les résultats. | LLM à chaque tick / événementiel / règles déterministes. | Résultat collectif *et* tokens, watts si disponibles, durée. |
| **H8 — robustesse** : une interaction séduisante à l'écran n'est pas nécessairement stable ni généralisable. | Seeds, ordres d'exécution, prompts, modèles, scénarios tenus à l'écart. | Distributions de résultats et sensibilité aux perturbations. |

**Angle de recherche à privilégier :** la *distinction entre émergence réelle et comportements introduits par le concepteur*. Une élection, une religion, un marché ou une rumeur ne constituent pas une découverte si le phénomène est déjà imposé par le prompt, par le moteur, par le jeu utilisé, ou inféré subjectivement en regardant une seule simulation.

### Scénarios d'essai progressifs

1. **Invitation / fête** : annoncer un événement à un agent, observer diffusion, réponses et présence effective ; mesurer les oublis et les conflits d'agenda.
2. **Rumeur et correction** : injecter une information fausse *identifiée comme telle dans le moteur*, laisser circuler, puis injecter une preuve contraire ; mesurer contamination, correction et provenance.
3. **Coopération sous ressources limitées** : tâche impossible seul, matériaux contraints, échanges permis ; observer coordination et échecs.
4. **Conflits de normes et de préférences** : objectifs contradictoires ; mesurer négociation, sur-politesse et qualité de résolution.
5. **Choc externe contrôlé** (phase avancée) : pénurie, fermeture d'une route, absence d'un agent ; répéter avec un groupe témoin.

Ne pas débuter par un grand monde Minecraft. La simplicité d'un environnement abstrait permet de savoir **pourquoi** les résultats changent.

## 2. Protocole scientifique et métriques

**Comparaisons obligatoires :**
- **B0** : agents entièrement déterministes, règles explicites ;
- **B1** : LLM sans mémoire durable ;
- **B2** : LLM + mémoire, sans réflexions ;
- **B3** : LLM + mémoire + réflexions ;
- **B4** : B3 avec vérification explicite des faits et traçage de leur origine ;
- **B5** : architecture hybride, LLM sollicité sur des événements importants seulement.

**Méthode :** préenregistrer hypothèses, sorties attendues, métriques et seuils ; réutiliser cartes, objectifs, règles et états initiaux entre conditions ; conserver seeds, modèle et version exacte, prompts, température, quantification et budgets. Plusieurs répétitions par condition, comparaison des distributions, tailles d'effet et intervalles de confiance. L'ordre d'exécution et la génération GPU pouvant être non déterministes, un seed **ne garantit pas** un replay identique : journaliser ou rejouer les décisions LLM enregistrées.

**Mesures comportementales :** délai/portée/fidélité d'une rumeur ; taux de rappel, de contradiction et d'hallucinations ; taux d'actions valides ; réussite et ponctualité ; développement de relations ; fréquence des conflits et négociations ; diversité des décisions.

**Mesures systémiques :** tokens par jour simulé, temps réel par jour simulé, nombre d'appels, tokens/s utiles, p50/p95 des temps de réponse, pic RAM/VRAM, erreurs JSON, tentatives et reprises, consommation énergétique si mesurable. **Séparer qualité narrative, validité factuelle, réalisme social perçu et capacité réelle de prédiction.**

**Contrôles de validité :** évaluations humaines en aveugle lorsque le critère est qualitatif ; scénarios de validation jamais utilisés pour ajuster les prompts ; journal complet des erreurs ; publier aussi les expériences décevantes. Pas de chiffres fictifs pour les « gains » ou le nombre d'agents supportés.

## 3. Architecture du laboratoire

```text
scenario.yaml (carte, population, seed, lois, hypothèse testée)
       |
Moteur événementiel autoritaire : temps, position, ressources, permissions
       |  observations vérifiables
       v
Agent = persona + objectifs + mémoire épisodique (faits sourcés)
       + récupération + réflexion périodique + planification
       |
Adaptateur LLM -> action JSON contrainte -> validation du moteur
       |
Journal horodaté des événements -> checkpoint/replay -> métriques/rapports
       |
Vue 2D / graphe social / chronologie (facultatifs)
```

**Décisions d'ingénierie :**
- L'environnement est **source de vérité**. Une IA ne crée ni pièce, ni toilettes, ni nourriture en l'affirmant ; ses actions sont vérifiées contre l'état du monde. Les croyances erronées restent possibles et observables.
- **Un modèle partagé peut servir plusieurs agents** ; chaque agent conserve son contexte et sa mémoire séparés. Vingt-cinq agents ne signifient pas vingt-cinq modèles chargés en VRAM.
- Boucle **événementielle**, agents inactifs non interrogés inutilement, files de requêtes, batching lorsque pertinent, limite de tokens par expérience, pause/reprise.
- Stocker les souvenirs avec **date, source, type** (perception, ouï-dire, inférence), niveau de confiance ; comparer recherche simple/SQLite-FTS/embeddings. Éviter d'enregistrer des raisonnements internes cachés.
- Actions en **JSON validé**, retries plafonnés et fallback déterministe ; tester d'abord les contraintes et le moteur sans LLM.
- Backend d'inférence interchangeable (CPU, GPU local, station pro, API témoin optionnelle) ; monde et protocole identiques pour comparer les conditions.
- Séparer **interface spectaculaire** et simulation headless. Les résultats scientifiques ne dépendent pas d'une animation.

## 4. Palier A : machine modeste

**Profil expérimental :** 16 à 32 Go de RAM, GPU de l'ordre de **12 Go de VRAM** ; fonctionnement CPU seul possible pour des micro-scénarios plus lents. Exemple de classe matérielle : RTX 3060 12 Go.

**Candidats à mesurer**, sans sélection imposée : LLM instruct ouverts **3B à 8B** (p. ex. Qwen3-8B en quantification adaptée), servis par **llama.cpp / llama-server** au format GGUF ; modèles plus petits si le débit ou le contexte est limitant. Vérifier licence et compatibilité de la variante exacte.

- **MVP : 3 à 8 agents**, quelques lieux et tâches ; décider si la mémoire/reflexion a une valeur observable.
- **Ensuite : 25 agents**, mais **pas nécessairement en temps réel**. Appels séquencés et événements rares ; la métrique prioritaire est le coût pour simuler une journée, pas 25 agents « connectés simultanément ».
- Arbitrages : contexte court vs récupération ciblée ; fréquence des réflexions ; CPU/GPU offload ; cache ; politique hybride.
- **Critère de passage :** action/événement rejouable, erreurs mesurées, comparaison avec baselines et profiling stable. Aucun débit ni budget électrique annoncé avant expérimentation.

## 5. Palier B : station dite « professionnelle »

**Profil expérimental :** station de travail avec **64 à 128 Go de RAM**, un ou plusieurs GPU totalisant typiquement **48 à 80 Go de VRAM** ou davantage. GPU professionnels ou datacenter selon disponibilité ; aucune hypothèse de matériel déjà acheté.

**Candidats à mesurer :** classes **14B–32B** pour commencer ; **70B quantifié** seulement si la marge VRAM/contextes concurrents est vérifiée, typiquement sur configuration 80 Go ou multi-GPU adaptée. **vLLM** ou **SGLang** à comparer pour batching continu, cache de préfixe et gestion de plusieurs requêtes ; pas de promesse de supériorité sans benchmark.

- Répliquer **exactement** les expériences du palier A avec mêmes scénarios/mesures, puis comparer 8B vs 14/32B et architectures mono-agent/role-spécialisé.
- Passer de **25 à 50/100/200 agents** progressivement *sous condition de performance*. Tester 1 000 agents seulement après preuve de débit et avec stratégie événementielle/hybride. Ne pas confondre nombre d'agents persistés et nombre de générations simultanées.
- Nouveaux objets d'étude : réseaux sociaux multiples, microéconomie mesurable, information conflictuelle, coordination à grande échelle, robustesse inter-modèles.
- Comparer **coût–qualité–taille** à budget de tokens égal, puis budget matériel/temps égal ; ne pas privilégier arbitrairement le plus gros modèle.

**Note physique utile :** à 4 bits, les poids théoriques occupent environ **0,5 octet/paramètre** avant quantification réelle et surcoûts : ~4 Go pour 8B, ~16 Go pour 32B, ~35 Go pour 70B. Il faut **ajouter** KV-cache, contexte, runtime, métadonnées et marge de parallélisme : ces chiffres ne sont **pas** des exigences VRAM suffisantes. Plus d'agents accroît surtout le **nombre de requêtes et de tokens**, pas forcément le nombre de copies du modèle.

**Hypothèse coûteuse mais intéressante :** une société de petits modèles, avec un moteur strict, de bons souvenirs et quelques agents/événements confiés à un modèle plus puissant, peut battre la configuration « gros LLM pour chaque action » en qualité **par euro/jour simulé**. Elle mérite un test dédié.

## 6. Roadmap en baby steps

> **Important :** ce tableau est un plan futur, pas le journal de travaux de l'incubateur. Avant le premier développement, benchmark ou expérimentation du laboratoire, créer le dépôt dédié et retirer cette fiche de l'index. Une revue bibliographique de cadrage peut rester ici tant que l'idée n'est pas lancée.


| Étape | Sous-étapes | Critère observable | Statut |
|---|---|---|---|
| **P0 — préparation** | Lire Smallville, Concordia, AgentSociety 2 ; vérifier licences ; figer 2–3 scénarios et mesures ; choisir premier modèle. | Protocole et comparaison des moteurs consignés. | À faire |
| **P1 — moteur minimal** | Carte abstraite, horloge, lieux, ressources, événements, journal/replay, baseline B0. | Tests de contraintes et replay identique sans LLM. | À faire |
| **P2 — POC modeste** | 3–8 agents, mémoire sourcée, planification, JSON, inférence locale, premiers profils coût. | Scénario complet et métriques exploitées. | À faire |
| **P3 — science** | Ablations B0–B5, rumeur, invitations, répétitions, graphiques et critique des biais. | Rapport négatif ou positif reproductible. | À faire |
| **P4 — 25 agents** | Même protocole, variation modèles/quantification, mesure de la limite machine A. | Rapport « niveau Smallville » avec coûts et limites. | À faire |
| **P5 — station pro** | Bench 14–32B, batching, 25→50→100+ agents, tests de rareté/cooperation. | Frontière coût/qualité/échelle et sensibilité. | À faire |
| **P6 — publication** | CI, données synthétiques, méthodes et évaluations, interface 2D facultative. | Rapport de recherche et résultats du **dépôt dédié**, avec hypothèses non confirmées explicitement signalées. | À faire |

**Premier sous-pas proposé :** réaliser une **revue critique de trois moteurs** (code Stanford de 2023, Concordia, moteur minimal ad hoc), écrire le scénario d'invitation et ses critères de succès, puis créer un **simulateur déterministe sans IA**. Ne pas coder une ville entière avant de savoir comment évaluer les agents.

**Stop/go :** ne pas augmenter la population ou la taille du LLM tant que les baselines, l'instrumentation et les coûts par journée simulée ne sont pas mesurés. Les seuils chiffrés seront définis au moment du premier benchmark.

## 7. Risques et éthique

- **Plausible ≠ prédictif** : les LLM imitent des régularités du langage, pas nécessairement celles d'une population réelle.
- **Homogénéité du modèle** : 100 agents fondés sur un même LLM ne sont pas 100 observations humaines indépendantes. Contrôler sur-politesse, conformisme et biais.
- **Hallucinations contagieuses** : conserver la vérité du moteur et les croyances des agents séparément, mesurer provenance et correction.
- **Fuite des résultats** : ne pas adapter le prompt aux scénarios réservés à l'évaluation.
- **Données personnelles** : uniquement identités et corpus synthétiques par défaut ; pas de clonage de personnes réelles, données sensibles ou tests de manipulation de groupes sans base légale, consentement et validation éthique.
- **Licences** : vérifier avant de recopier code, assets, modèles ou personnages originaux ; pas de clés API dans un dépôt public.
- **Énergie et coût** : rapporter le coût total d'une expérience, pas seulement la taille des modèles.

## 8. Références vérifiées (2026-10-26)

- [Park et al., Generative Agents (2023)](https://arxiv.org/abs/2304.03442) et [GitHub officiel Smallville](https://github.com/joonspk-research/generative_agents) : point de départ, environnement et code d'époque (dépendances/API à revisiter).
- [Google DeepMind, Concordia](https://github.com/google-deepmind/concordia) : agents et moteur « Game Master », simulations sociales génératives.
- [Tsinghua, AgentSociety 2](https://github.com/tsinghua-fib-lab/agentsociety) et [article AgentSociety 2 (2026)](https://arxiv.org/abs/2607.11895) : framework actuel. [Article 2025 AgentSociety 1](https://aclanthology.org/2025.acl-industry.94/) : les simulations à très grande échelle ont nécessité une infrastructure de **24 GPU A800**, à ne pas extrapoler à un PC local.
- [llama.cpp — serveur](https://github.com/ggml-org/llama.cpp/blob/master/tools/server/README.md) ; [vLLM](https://docs.vllm.ai/en/latest/) ; [Qwen3-8B, fiche modèle](https://huggingface.co/Qwen/Qwen3-8B) : pistes d'inférence et de modèle, **non benchmarkées ici**.
- [Vidéo à l'origine du projet](https://www.youtube.com/watch?v=jRBUHrusAyk) : vulgarisation, pas source de validation scientifique.

## 9. À transmettre à Codex

- **Statut strict :** cadrage scientifique uniquement, aucun code ni résultat. Ne pas créer de repo d'implémentation ni annoncer de benchmarks sans nouvelle décision.
- **Priorité recherche + ingénierie :** protocoles falsifiables, reproductibilité, baselines, monde autoritaire, profils matériel A/B et coût mesuré ; interface graphique secondaire.
- **Prochaine décision :** sélectionner l'architecture de P1 et le modèle de P2 après revue technique et de licences.
- **Suite Git :** dès la décision de lancer une recherche appliquée, une expérimentation ou un POC, créer un dépôt autonome avec `AGENTS.md` et journal de contexte, y transférer la fiche puis **supprimer** la fiche et son lien dans l'incubateur. Ne pas attendre l'existence d'un POC pour le faire.
