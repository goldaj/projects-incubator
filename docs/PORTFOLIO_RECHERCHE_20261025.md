# Audit scientifique du portefeuille — 25 octobre 2026

**Périmètre : les 36 fiches de projet du dépôt, sept domaines, plus leurs
dépôts autonomes lorsqu'ils existent.** Revue documentaire et revue de code
ciblée des quatre travaux retenus ; **pas** une reproduction exhaustive
de toutes les archives ni une évaluation de leur viabilité commerciale.

## Principe : matière ≠ preuve

- **Matière** : source, manuscrit, protocole, prototype, dataset licite,
  tests, limites connues. L'existence d'une centaine de pages peut témoigner
  d'un effort intellectuel réel, pas de la validité de l'hypothèse.
- **Preuve** : expérience reproductible et contradictoire, critères de
  succès et d'échec fixés **avant** les nouveaux résultats.
- **Transfert** : un prototype historique ne devient ni une production
  prête à déployer, ni une étude validée simplement en changeant de dépôt.
- **Sécurité** : tout contenu de manuscrit, configuration de compte, clé,
  réponse privée de lecteur, donnée financière personnelle ou poids de
  modèle reste hors de cet incubateur **public**.

La priorité est qualitative : corpus concret existant, questions
falsifiables, mécanisme de validation faisable, valeur de la prochaine
expérience et risque de casser l'historique. Elle ne constitue pas une
note scientifique objective ou un préjugé de rentabilité.

## Priorité de recherche : quatre projets riches

| Rang | Sujet / dépôt de référence | Matière vérifiée | Lacune déterminante | Livrable proposé en branche séparée |
| --- | --- | --- | --- | --- |
| 1 | [TRAME](https://github.com/goldaj/trame-chartist-research) | 14 documents / 102 p., plusieurs audits de codecs sur observations passées, scripts et protocoles ; aucun modèle prédictif | Comparaison **prospective** contre des témoins sérieux en prix natifs, sans fuite ni fausse indépendance des fenêtres | [Protocole + scoreur synthétique, PR #1](https://github.com/goldaj/trame-chartist-research/pull/1) |
| 2 | [Inference Companion Lab](https://github.com/goldaj/inference-companion-lab) | charte normative, rapport, politique de sûreté, scénarios A/B/C/D, machine témoin ; aucun observateur exécuté | Modèle/engine non choisis, QoS non calibrée, effet observateur non mesuré | [Protocole de falsification A0/A1 et A/B/C/D, PR #1](https://github.com/goldaj/inference-companion-lab/pull/1) |
| 3 | [Le garçon et la libellule](https://github.com/goldaj/le-garcon-et-la-libellule) **privé** | Manuscrit V3.2, contrôles, storyboard, maquettes, panels simulés | Lecteurs **humains naïfs** et impression ; préserver toute énigme sensible | [Protocole terrain et fiche vierge, PR #1](https://github.com/goldaj/le-garcon-et-la-libellule/pull/1) |
| 4 | [Crypto Price ML Experiments](https://github.com/goldaj/crypto-price-ml-experiments) **privé** | Modèles historiques, indicateurs et tests, code récupéré | Labels terminaux artificiels, imputation pré-split, causalité des features et holdout | [Audit + baselines synthétiques, PR #1](https://github.com/goldaj/crypto-price-ml-experiments/pull/1) |

Ces quatre dépôts **existent déjà** : il n'est donc pas nécessaire de
créer de nouveau dépôt pour en sortir les travaux de l'incubateur.
Les PR sont des **propositions non fusionnées**. Aucun gain prédictif,
d'inférence ou de compréhension des lecteurs n'est revendiqué.

### Ordre des preuves, pas ordre de prestige

1. **TRAME** : protocole figé, hypothèse falsifiée ou non, expérience
   réellement hors échantillon ; résultats de reconstruction ≠ prévision.
2. **Inference** : coûts et risques de mesure connus, modèle imposé
   sélectionné, observateur seulement **après** gel du protocole v0.1.
3. **Livre** : autorisation parentale pour mineurs, maquette sans secret,
   rubriques fixées, mesures de personnes réelles ; un panel fictif
   n'est pas un « n = 18 ».
4. **Crypto ML** : d'abord éliminer les mécanismes de fuite et produire
   des baselines de série chronologique ; n'entraîner les gros réseaux
   qu'après les tests négatifs élémentaires.

## Deuxième vague : de la matière, mais le verrou est différent

| Sujet | Stade d'après la fiche | Prochaine preuve intéressante |
| --- | --- | --- |
| [Résurrectés](../creatif-et-ecriture/resurrectes.md) | Premier jet complet, code éditorial, dépôt privé | Audit de continuité et lecture aveugle d'un extrait, pas un autre panel IA |
| [Novel Writing Toolkit](../creatif-et-ecriture/novel-writing-toolkit.md) | Outils génériques déjà extraits | Tests sur manuscrit factice long et robustesse de l'assemblage, dans son dépôt |
| [Prototypes de jeux Python](../jeux/python-game-prototypes.md) | Plusieurs boucles réellement codées | Tests utilisateurs des boucles complètes, rétention / compréhension observées |
| [Le Président utile](../creatif-et-ecriture/le-president-utile.md) | Manuscrit existant v1.1 | Audit contradictoire proposition → mécanisme → source → objection ; ne pas confondre opinion et validation |
| [Twitch Pokémon](../ia-et-multimedia/twitch-pokemon-chat-bot.md) | Code historique dans dépôt dédié | Test Windows/Twitch réel, après tests réseau simulés |
| [Eclaire](../creatif-et-ecriture/eclaire-animated-pet.md) | Assets et dépôt dédié | Essai d'animation, lisibilité/engagement par utilisateur réel |

**Archives/implémentations ayant déjà leur dépôt propre**, à maintenir
en priorité chez elles plutôt que recopier ici : Binance Strategy,
Bitcoin Wallet Education, dYdX (historique), Hyperliquid Streamlit
(historique), Android Widget, Angular Training, Programming Experiments.
Le projet *Hyperliquid actuel* est totalement hors périmètre de cette
revue ; aucun ordre ni déploiement n'a été lancé.

## Fiches à faible matière autonome : ne pas précipiter un dépôt

Pour l'instant essentiellement des **concepts** : Anicompass,
Media Backlog, DeckLab, Idle Game, VTube Physics Lab, PO Forge,
Decision Board, StoryGrid-24, France 2040, La sauvegarde impossible,
Jade Cloud 24/7, Live2D Remote Lab, Server Monitor Dashboard,
Twitch Streamer Dashboard, Assistant AR Japan Snapchat,
Deep Tech Watch, Château Business Plan, Crypto Trading Research.

Une simple fiche de 400 à 500 caractères n'est pas une hypothèse
scientifique qualifiée. La suite pertinente avant le code :

| Concept | Test sans nouveau dépôt | Décision après test |
| --- | --- | --- |
| Decision Board | 3 décisions synthétiques, stabilité des classements quand les poids changent, biais des évaluateurs | Extraire si la sensibilité est explicable et l'usage PO utile |
| DeckLab | Une économie de cartes reproductible issue de cartes fictives, simulation d'équilibrage avant moteur UI | Extraire seulement si les données/contraintes et critères existent |
| Anicompass | Mini jeu de recommandations publiques, experts masqués au classement, mesure de pertinence et diversité sans profil personnel | Extraire si une baseline simple est battue |
| Live2D Remote Lab | Contrat d'animation, licence et assets démo **autorisés**, test de rendu/décodage hors caméra | Extraire si un vrai visualiseur indépendant des secrets Jade tourne |
| Deep Tech Watch | Corpus de sources datées, annotation fait/projection/incertitude, validation des alertes et dédoublonnage | Extraire quand la traçabilité automatique est testée |

Les autres idées méritent une proposition de problème utilisateur et
un corpus accessible avant toute génération de code. Une promesse
d'innovation sans protocole reste une intention.

## Gate de sortie de l'incubateur vers un nouveau dépôt

Une idée **sans dépôt existant** ne sera candidate à promotion que si
elle dispose de tous les éléments suivants :

1. Problème et bénéficiaire clairement spécifiés.
2. Matériel licite : données, assets ou corpus reproductible.
3. Hypothèse principale **et** expérience qui peut conclure négativement.
4. Une baseline simple, des résultats observés et une limite explicite.
5. Un prototype réellement exécutable ou un artefact de recherche autonome
   (avec commandes de reproduction), pas un répertoire de README.
6. Un nom et un périmètre qui ne dupliquent pas un dépôt autonome existant.
7. Validation de sécurité/confidentialité/licences et feu vert du
   propriétaire pour créer le nouveau dépôt.

**Bilan actuel : 0 nouveau dépôt à demander**, puisque les quatre
priorités possèdent déjà le leur et les concepts nouveaux ne satisfont
pas encore le gate. Les nouveaux travaux sont proposés en branches
pour Codex ; les mains courantes et protocoles originaux restent intacts.

## Sources de méthode

- Rolling origin et données futures non accessibles au fitting :
  https://otexts.com/fpp3/tscv.html
- Pièges classiques d'évaluation de prévision :
  https://doi.org/10.1007/s10618-022-00894-5
- Benchmark d'inférence et définition d'une charge reproductible :
  https://github.com/mlcommons/inference
