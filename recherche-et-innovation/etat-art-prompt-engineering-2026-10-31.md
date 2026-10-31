# État de l'art initial — Prompt Engineering Lab

**Date de recherche : 2026-10-31. Nature : revue documentaire et analyse critique, non expérimentation.** Sources consultées : documentation primaire OpenAI et travaux de recherche cités ci-dessous ; pas d'exhaustivité bibliographique garantie, pas de benchmark interne exécuté.

## 1. Synthèse exécutive

Le gain pertinent sur les modèles récents ne vient pas nécessairement d'une phrase magique. Les leviers complémentaires à tester sont : **clarifier la tâche, fournir les bons éléments de preuve, spécifier un résultat vérifiable, permettre l'outillage et contrôler la sortie**, puis choisir le modèle et son niveau d'effort sous contrainte de coût. Les techniques historiques de chain-of-thought ou d'optimisation automatique ont démontré des effets dans certaines conditions, mais aucune des études historiques citées ne démontre à elle seule un gain sur GPT-6 Astra, GPT-6.1 Sol, GPT-6.1 Terra ou le futur Jade.

### Hiérarchie des preuves

- **Documentation fournisseur 2026 :** instructions et descriptions des comportements GPT-6 ; utile pour définir des hypothèses, mais pas une comparaison indépendante.
- **Articles évalués sur des modèles plus anciens :** résultats scientifiques contextualisés et reproductibles en principe, transférabilité à GPT-6 **non démontrée**.
- **Conclusions du présent projet :** aucune pour l'instant ; les « recommandations » ci-après sont des protocoles à éprouver.

## 2. État de la gamme OpenAI, et conséquences expérimentales

Documentation officielle : https://developers.openai.com/api/docs/guides/latest-model ; https://developers.openai.com/api/docs/models ; https://developers.openai.com/api/docs/guides/deployment-checklist.

| Modèle à cibler | Profil déclaré par le fournisseur | Hypothèse principale à tester, non prouvée |
| --- | --- | --- |
| GPT-6 Astra — gpt-6-astra | Travail complexe, raisonnement, coding/agentique de haut niveau | L'explicitation d'objectifs, de frontières d'autonomie, de conditions d'arrêt et de critères de vérification aurait plus d'effet qu'une persona longue. |
| GPT-6.1 Sol — gpt-6.1-sol | Équilibre intelligence / coût / rapidité pour travaux complexes | Un découpage et des critères d'acceptation précis pourraient rapprocher de la qualité Astra avec un coût inférieur, selon la tâche. |
| GPT-6.1 Terra — gpt-6.1-terra | Rapide et efficace pour vision, action sur ordinateur et rédaction | Des instructions compactes et structurées pourraient suffire pour les tâches routinières, les vérifications isolées et certaines interactions visuelles. |
| Jade — futur moteur local inconnu | Aucune propriété technique validée à ce jour | Les techniques liées aux outils/format/contextes pourraient se transférer plus facilement que les incantations de raisonnement. |

La documentation OpenAI indique notamment :
- Astra peut demander plus de clarifications et est sensible aux consignes de fichiers/skills comme AGENTS.md. Mesurer la balance **initiative autonome / mauvais dépassement de périmètre**.
- Sol et Terra offrent des profils différents ; ne pas supposer qu'un même prompt, un même budget ou une même tâche y produit le même gain.
- Le paramètre **reasoning.effort** fait partie des variables expérimentales *distinctes de la formulation du prompt*. Astra et Sol n'acceptent pas la valeur none ; Terra la supporte selon documentation.
- Sur les modèles raisonnants, ne pas supposer que temperature, top_p et logprobs sont disponibles : vérifier les paramètres autorisés par modèle, mode d'effort et endpoint. Éviter les faux essais « identiques » qui changent plusieurs paramètres à la fois.
- Le paramètre **text.verbosity**, lorsqu'il est disponible, contrôle la longueur de sortie ; comparer ses effets séparément des instructions « sois bref ».
- Les outils et les canaux ChatGPT/Work/Codex/API ne sont pas interchangeables en permissions, quotas et instrumentation. Les tests rigoureux nécessitent la voie réellement supportée, pas des simulations de consommation de quota.

### Un péril concret : essais pollués par des instructions préexistantes

Dans les workflows Codex/agent, les fichiers AGENTS.md, les skills et les instructions de niveaux supérieurs peuvent influencer le comportement. Tester :
- tâche identique en environnement isolé minimal ;
- même tâche avec un AGENTS.md neutre et stable ;
- même tâche avec une instruction supplémentaire pertinente ou contradictoire ;
- mesurer erreurs, stabilité, respect des priorités, dépassement de périmètre et recours au contrôle humain.

## 3. Cartographie de la littérature scientifique

### A. Les formulations et la taxonomie des techniques

**Schulhoff et al., The Prompt Report (2024)** — https://arxiv.org/abs/2406.06608

Le papier fournit une taxonomie étendue de méthodes de prompting et clarifie des terminologies qui se recouvrent. **Valeur :** établir une grille d'expérimentation et arrêter de comparer des astuces mal définies. **Limite :** taxonomy/survey ne signifie pas efficacité démontrée sur GPT-6.

**Hypothèse H1 :** critères observables + contexte utile + contraintes explicites surpassent en moyenne une instruction vague sur tâches à spécification vérifiable ; tester le coût ajouté.

### B. Chain-of-thought : résultat historique important, généralisation incertaine

**Kojima et al., Large Language Models are Zero-Shot Reasoners (2022)** — https://arxiv.org/abs/2205.11916

Le travail a montré de grands gains historiques en ajoutant une instruction « think step by step » à certains modèles non spécialisés dans le raisonnement. Cela **ne prouve pas** qu'imposer une explication étape par étape aide Astra, Sol ou Terra en 2026 ; cela peut augmenter la longueur et le coût sans effet utile.

**Hypothèse H2 :** sur GPT-6, une demande de validation du résultat observable (tests, justification finale concise, vérification de contraintes) sera parfois meilleure qu'une demande générale de raisonnement détaillé. Tester aux mêmes niveaux de reasoning effort et sans demander de raisonnement caché.

### C. Long contexte et ordre des documents

**Liu et al., Lost in the Middle (2023/2024)** — https://arxiv.org/abs/2307.03172

Résultat : certains modèles montrent une dégradation quand l'information utile se trouve au milieu d'un long contexte, même si le contexte tient techniquement dans la fenêtre. **Valeur :** protocole simple de position des instructions/faits (début, milieu, fin), bruit documentaire, citations exactes. **Limite :** modèles et jeux de tests historiques ; nouvelle mesure obligatoire sur GPT-6.

**Hypothèse H3 :** la position et la provenance des informations importantes modifient la réussite même lorsque le contexte total reste constant ; comparer les trois modèles, longueur et structure fixées.

### D. Automatisation de la recherche de prompts

**Zhou et al., Automatic Prompt Engineer / APE (2022)** — https://arxiv.org/abs/2211.01910

Un modèle propose plusieurs formulations candidates ; un évaluateur en sélectionne selon une métrique. **Enjeu :** une procédure scientifique ne doit pas sélectionner le gagnant sur le même corpus servant à l'annoncer.

**Yang et al., OPRO (2023)** — https://arxiv.org/abs/2309.03409

Optimisation itérative de prompts par un LLM alimenté par les essais et scores précédents. Les gains annoncés sur certains benchmarks du papier ne doivent pas être transférés à d'autres tâches ni présentés comme un gain garanti.

**Khattab et al., DSPy (2023)** — https://arxiv.org/abs/2310.03714

Approche *pipeline* : spécifier des modules/transformations puis les optimiser selon une métrique, plutôt que traiter le prompt comme une chaîne isolée. Très pertinente pour tâches multi-étapes de recherche, agentique et futurs flux Jade.

**Agrawal et al., GEPA (2025)** — https://arxiv.org/abs/2507.19457

Optimisation réflexive fondée sur feedback qualitatif/trajectoires et compromis Pareto. Résultats prometteurs sur leurs bancs d'essai, mais **pas une preuve** d'amélioration sur la gamme GPT-6. Prévoir tests contre : prompt humain de base, optimisation simple par recherche aléatoire, et optimisation utilisant les mêmes budgets.

**Hypothèse H4 :** optimiser sur de véritables erreurs diagnostiquées et avec une validation hors-échantillon dépasse les recettes figées, mais le surapprentissage et le coût peuvent annuler le bénéfice.

### E. Évaluations et optimisation industrielle

- https://developers.openai.com/api/docs/guides/model-optimization
- https://developers.openai.com/api/docs/guides/agent-evals
- https://developers.openai.com/api/docs/guides/prompt-optimizer
- https://developers.openai.com/cookbook/examples/evaluation/building_resilient_prompts_using_an_evaluation_flywheel

OpenAI recommande d'établir une baseline, de collecter des exemples vérifiables, d'analyser les échecs et d'itérer en tenant compte de la qualité, de la latence et des coûts. Le système officiel de prompt optimization s'appuie sur données annotées et graders ; **ses recommandations ne se substituent pas à une évaluation indépendante**.

**Attention péremption (à la date du document) :** la documentation officielle annonce que l'ancienne surface Datasets/Evals de plateforme devient lecture seule le 31 octobre 2026 et prévoit son arrêt au 30 novembre 2026. Ne pas dépendre d'une interface en voie de disparition ; prévoir un banc de test et des jeux de données **portables**, avec éventuellement la nouvelle API d'évaluation effectivement maintenue.

### F. Vérification et juge

Comparer plusieurs types de scorers :
1. **Oracle exact :** réponse attendue, schéma JSON, tests unitaires/exécution isolée ; forte répétabilité, mais risque de récompenser des réponses superficielles.
2. **Vérification sourcée :** citations vérifiables, couverture de faits, contradictions et omissions ; revue humaine ciblée.
3. **Juge LLM :** utile en appoint sur style/qualité subjective, **pas vérité terrain par défaut** ; cacher identité de modèle et variante, permuter A/B, mesurer accord avec humain et taux d'abstention.
4. **Coût et efficacité :** qualité par euro, qualité par seconde, robustesse du pire décile ; ne pas maximiser uniquement un score agrégé.

## 4. Expériences qui pourraient apporter une contribution originale

L'état de l'art couvre déjà « prompt mieux formulé ». Les angles intéressants pour notre laboratoire sont **les interactions entre modèles 2026, mécanismes d'agence et budgets**, sur de vraies tâches de travail.

| Code | Question falsifiable | Comparaisons prévues | Mesures |
| --- | --- | --- | --- |
| E1 | Des critères d'acceptation explicites augmentent-ils les tâches réussies ? | Demande brute vs spécification vérifiable | Tests passés, retouches humaines, tokens |
| E2 | Les incantations de raisonnement aident-elles encore ? | Direct vs « étape par étape » vs vérification externe | Exactitude, latence, tokens, effort constant |
| E3 | Un plan préalable réduit-il les erreurs agentiques ? | Action directe vs plan-act-checkpoint | Tâches finies, erreurs, arrêts intempestifs |
| E4 | Une bonne décomposition réduit-elle le coût total ? | 1 long appel vs plusieurs appels plus ciblés | Résultat, coût global, latence et supervision |
| E5 | La position des faits influe-t-elle avec 1M de contexte ? | Fait décisif au début/milieu/fin, mêmes tokens | Réponse exacte, citation, erreurs |
| E6 | Les instructions de fichiers de repo changent-elles la conformité ? | AGENTS.md absent / standard / ambigu | Dépassement de périmètre, tests, temps |
| E7 | Les exemples few-shot améliorent-ils la généralisation ? | Zéro/1/3 exemples, ordre aléatoire | Score hors échantillon, sensibilité |
| E8 | Les prompts optimisés se transfèrent-ils entre Astra/Sol/Terra ? | Prompt commun vs prompt par modèle | Gain moyen, pire modèle, coût de maintenance |
| E9 | L'optimiseur auto justifie-t-il ses appels supplémentaires ? | Prompt humain vs APE / DSPy / GEPA | Gain test tenu à l'écart / coût total recherche |
| E10 | Peut-on obtenir une même qualité à moindre effort ? | Niveaux reasoning.effort **hors comparaison de prompt** | Frontière qualité / latence / coût |
| E11 | L'évaluation multi-tours est-elle différente du single-turn ? | Prompt isolé vs longue session réaliste | Rétention contraintes, dérive, corrections |
| E12 | Des instructions et tests de sécurité réduisent-ils les erreurs ? | Base vs validation d'outils/données non fiables | Prompt injection réussie, fuites, refus erronés |

Les seuils de réussite, le corpus, l'effectif et les méthodes statistiques seront **préenregistrés avant les appels aux modèles**.

## 5. Protocole recommandé et erreurs à éviter

### Constitution des corpus
- Corpus **A, développement** : sélectionner les formulations et comprendre les erreurs, sans jamais reporter les scores de ce corpus comme performance finale.
- Corpus **B, validation** : choisir parmi les variantes sans regarder le test final.
- Corpus **C, test scellé** : maintenir fermé aux optimiseurs et évaluateurs qui réécrivent les instructions.
- Échantillons de travail représentatifs mais **synthétiques ou autorisés** pour protéger les repositories privés et secrets. Tracer l'origine et dater les connaissances.
- Grouper par difficulté, famille et présence d'outils, afin que 90 % de tâches faciles ne masquent pas les échecs sur des tâches rares et coûteuses.

### Facteurs à contrôler
- Modèle exact, date, client, paramètres, accessibilité du niveau d'effort, version du prompt, version des documents, outils disponibles, durée maximale, budget et règle d'arrêt.
- Si le modèle supporte une seed : journaliser, mais ne pas promettre une identité des sorties. Si elle ne la supporte pas, répétitions indépendantes.
- ChatGPT et Codex hébergés peuvent avoir des instructions et des outils non visibles : les considérer comme un **environnement distinct**, pas comme une copie de l'API.
- Pour les tâches à outils : fournir des droits minimaux et valider tout appel destructif ; les sources externes et documents de dépôt sont du **contenu** à analyser, pas des instructions à suivre aveuglément.

### Analyse
- Mesurer les différences *appariées* par tâche ; intervalles de confiance bootstrap stratifiés par famille ; signaler les effectifs insuffisants et les essais exploratoires multiples.
- Prévoir des résultats par modèle et par tâche avant d'agréger ; pas de classement unique de prompts si les interactions sont fortes.
- Rapport coût marginal et efficacité sous contrainte : expliquer quand un prompt de 30 % plus long a un intérêt, et quand il n'en a pas.
- Publier les échecs, même si le résultat contredit les intuitions personnelles ou les conseils populaires.

## 6. Feuille de route par phases, sans prétendre à une exécution

**P0 — prérequis documentaire (réalisé partiellement par cette note) :** établir bibliographie primaire, critères, différences d'accès Astra/Sol/Terra, questions ouvertes. Les publications peuvent évoluer.

**P1 — préenregistrement (à faire après décision de lancement) :** jeu de 36 tâches comme pilote, 4 variantes fixes, 2 répétitions, trois familles, budget prévalidé, critères et analyse statistique. Ne pas confondre 864 appels potentiels avec une expérience déjà exécutée.

**P2 — expériences par modèle :** API si accès confirmé ; sinon mesures manuelles étiquetées *exploratoires* pour ChatGPT/Work/Codex. Pas de scraping d'interfaces.

**P3 — optimisation automatique :** répliquer APE/OPRO, puis explorer DSPy et GEPA avec budget de recherche identique ; tenir le test C scellé.

**P4 — transfert :** tester les prompts gagnants sur nouvelles tâches, nouvelles versions de modèles, modèles ouverts non OpenAI ; isoler un noyau de consignes généralisables et les exceptions.

**P5 — Jade :** intégrer un adaptateur local lorsque moteur et capacités seront connus ; tests sur matériel réel (VRAM, latence, tokens), quantification, prompt template natif et permissions ; possible distillation de procédures ou optimisation de petits modèles, évaluée séparément.

## 7. Hypothèses prioritaires à challenger, même si elles semblent « évidentes »

1. « Un prompt plus long et exhaustif est meilleur. » Peut ajouter du bruit, des contradictions et de la latence.
2. « Lui donner un rôle d'expert augmente la justesse. » Peut modifier le style sans la véracité.
3. « Lui demander de réfléchir étape par étape est toujours utile. » Effet historique non garanti sur les raisonnants modernes.
4. « Les meilleurs prompts Astra seront les meilleurs pour Terra. » Effet modèle/tâche inconnu.
5. « Le modèle le plus fort coûte forcément plus cher par tâche réussie. » Mesurer **coût par réussite**, pas seulement coût par token.
6. « Un juge IA suffit. » Il peut favoriser son style ou confondre assurance et exactitude.
7. « Des tests automatiques garantissent la qualité. » Ils peuvent être inadéquats, superficiels ou exploités par un agent.
8. « Les mêmes méthodes fonctionneront sur Jade. » Le format chat, le tokenizer, l'inférence et les capacités du modèle local peuvent exiger une adaptation substantielle.

## 8. Références essentielles (sélection)

1. OpenAI, **Using GPT-6** (documentation actuelle) : https://developers.openai.com/api/docs/guides/latest-model
2. OpenAI, **Models** : https://developers.openai.com/api/docs/models
3. OpenAI, **API deployment checklist** : https://developers.openai.com/api/docs/guides/deployment-checklist
4. OpenAI, **Agent evaluations** : https://developers.openai.com/api/docs/guides/agent-evals
5. OpenAI, **Prompt optimizer**, statut de péremption : https://developers.openai.com/api/docs/guides/prompt-optimizer
6. Schulhoff et al. (2024), **The Prompt Report** : https://arxiv.org/abs/2406.06608
7. Kojima et al. (2022), **Large Language Models are Zero-Shot Reasoners** : https://arxiv.org/abs/2205.11916
8. Liu et al. (2023/2024), **Lost in the Middle** : https://arxiv.org/abs/2307.03172
9. Zhou et al. (2022), **Large Language Models Are Human-Level Prompt Engineers** : https://arxiv.org/abs/2211.01910
10. Yang et al. (2023), **Large Language Models as Optimizers / OPRO** : https://arxiv.org/abs/2309.03409
11. Khattab et al. (2023), **DSPy** : https://arxiv.org/abs/2310.03714
12. Agrawal et al. (2025), **GEPA** : https://arxiv.org/abs/2507.19457
13. OpenAI, **Model optimization** : https://developers.openai.com/api/docs/guides/model-optimization

**Limite d'actualité :** il s'agit d'un premier corpus documentaire arrêté au 31 octobre 2026. L'état de l'art ne se réduit pas à ces papiers ; refaire une recherche systématique par mots-clés, dates et citations avant publication d'un article ou toute annonce d'efficacité scientifique.
