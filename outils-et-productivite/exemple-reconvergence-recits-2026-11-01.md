# Cas étalon — « Le bal, la clé et la fausse alarme » (fiction originale de test)

**But :** illustrer comment les routes de Romance Multiverse peuvent **se croiser, diverger, se revoir puis s'entremêler** en conservant des historiques divergents. **Ce document est un scénario méthodologique inédit, pas du contenu canonique du jeu ni un test logiciel exécuté.**

## 1. Le scénario

Personnages fictifs et **adultes** : **Mina** (organise le bal), **Ren** (ami et futur intérêt amoureux), **Sora** (enquête sur des anomalies). Trois fils principaux :

- **R :** romance / confiance entre le protagoniste et Ren.
- **E :** enquête sur une clé disparue et une porte du sous-sol.
- **H :** menace étrange et tonalité horreur, déclenchable après certaines découvertes.

Événement pivot commun : **le bal du vendredi à 21 h**. Tout le monde peut y être présent selon différentes histoires ; les personnages n'ont pourtant pas vécu les mêmes événements.

### Graphe logique réduit

```text
         PROLOGUE : une clé disparaît
              /                \
         Route R               Route E
      dire la vérité        cacher une preuve
      ou mentir à Ren       ou prévenir Sora
          \                     /
           \                 /
            BAL (PIVOT, variantes selon l'état)
             /              |             \
         confession     incident/enquête    horreur
             \              |              /
              \         CROISEMENT 2      /
               \       révélations        /
                \/          |           \/
                  choix final à effet durable
                    /        |        \
                  FIN R     FIN E      FIN H
```

Les **traits convergents** ne signifient PAS effacer l'état. La même scène `bal` choisit sa variante relationnelle et sa variante d'information ; le fait d'avoir poursuivi l'enquête peut changer la confession et vice versa.

## 2. État de jeu minimal (schéma conceptuel)

| Champ | Domaine | Rôle |
| --- | --- | --- |
| `key_location` | `missing / Ren / Sora / player` | Vérité du monde |
| `ren_trust` | entier borné `0..3` | Relation |
| `ren_knows_lie` | booléen | Connaissance du personnage Ren |
| `sora_knows_basement` | booléen | Connaissance de Sora |
| `threat_known_to_player` | booléen | Connaissance du protagoniste |
| `thread_R`, `thread_E`, `thread_H` | états `dormant/open/advanced/resolved` | Progression des fils |
| `time_slot` | `fri_18/fri_20/fri_21/fri_22` | Temps logique |
| `seen_events` | ensemble d'IDs stables | Histoire irréversible |

**Remarque :** la vérité et les connaissances sont des champs séparés. Dans un futur modèle, conserver aussi `unknown`, croyances erronées, sources et témoins.

## 3. Trois histoires arrivant au même événement

### Historique A — Confidence

Le protagoniste a dit la vérité à Ren ; `ren_trust=3`, `ren_knows_lie=false`, Sora n'a pas encore découvert le sous-sol. Au bal, Ren se montre chaleureux. Une invitation à danser est possible ; une option de mise en garde manque si le protagoniste n'a pas découvert la menace.

### Historique B — Trahison

Le protagoniste a menti, et Ren a trouvé la preuve ; `ren_trust=0`, `ren_knows_lie=true`. Même bal, mêmes portes, mais Ren coupe court à la conversation. Une **réconciliation** demande une action supplémentaire. Réutiliser textuellement la scène A serait une **incohérence narrative**.

### Historique C — Enquête infiltrée

Le protagoniste a travaillé avec Sora ; `sora_knows_basement=true`, `thread_E=advanced`. Au bal, Sora demande discrètement de vérifier la sortie de secours. L'ambiance est inquiète, même si l'action romantique reste disponible sous conditions.

**Intersection intéressante :** le scénario C peut coexister avec A ou B. Le jeu a donc un **produit de fils**, pas trois routes forcément mutuellement exclusives.

## 4. Exemple de contrat de jonction

**ID stable :** `JOIN_BAL_2100` ; type : rendez-vous partagé avec variantes.

- Préconditions **obligatoires** : `time_slot <= fri_21` et `Mina_present=true` (champ d'exemple à intégrer au schéma complet).
- Invariants : ne pas changer `ren_knows_lie` ou `sora_knows_basement` sans événement explicite ; conserver `ren_trust`.
- Sortie : `time_slot = fri_22`, événement `ball_attended` ajouté.
- Variante **Ren chaleureux** : `ren_trust >= 2` et Ren présent.
- Variante **Ren distant** : `ren_trust <= 1` et Ren présent.
- Variante **Sora alerte** : `sora_knows_basement`.
- Variante **Horreur** : `threat_known_to_player` ou autre déclencheur canonique prévu.
- Variante **de repli** : une description neutre compatible avec tous les états autorisés ; n'affirme aucun fait non démontré.
- Engagement narratif : les différences majeures des passés A/B doivent avoir **une conséquence observable** au bal ou avant la fin ; une scène neutre ne suffit pas si Ren est central.

Le validateur doit signaler si un état entrant n'a **aucune variante compatible** pour un personnage central, et empêcher l'usage d'un texte qui affirme une connaissance inexistante.

## 5. Démonstration d'un croisement qui change deux fils

Au bal, Sora donne à Ren une photographie du sous-sol uniquement si `sora_knows_basement=true` et `ren_trust >= 2`. L'événement `photo_shared` produit alors simultanément :

- enquête : une preuve décisive nouvelle ;
- romance : Ren comprend pourquoi le protagoniste était absent ;
- horreur : le protagoniste peut reconnaître une silhouette anormale.

Si `ren_trust=0`, le même échange échoue ou demande une réparation relationnelle ; la route de l'enquête n'est pas nécessairement bloquée : Sora peut trouver un autre interlocuteur. Les fils restent indépendants **mais se contaminent causalement**.

## 6. Tests à exécuter par le futur outil

| ID | Situation | Attendu |
| --- | --- | --- |
| U01 | A atteint `JOIN_BAL_2100` | Dialogue chaleureux cohérent ; pas de secret enquêté révélé à Ren |
| U02 | B atteint la même jonction | Ren ne prétend pas faire confiance au protagoniste |
| U03 | C et A combinés | Détection et jeu des répliques Sora + Ren compatibles |
| U04 | C et B combinés | Sora avance sans confesser automatiquement le secret à Ren |
| U05 | Ren absent | Aucune variante nécessitant Ren n'est exécutée |
| U06 | `key_location=missing` | Impossible de donner matériellement la clé à Sora |
| U07 | `ren_knows_lie=false` | Ren ne peut citer la preuve du mensonge comme acquise |
| U08 | Deux actes exigeant `time_slot=fri_21` dans des lieux disjoints | Conflit de présence signalé |
| U09 | Sortie d'un fil avec promesse `find_key` ouverte | Rapport d'obligation narrative non payée |
| U10 | Mise à jour de la confiance Ren | Tous les scénarios affectés de la jonction sont rejoués |
| U11 | Même scénario/graine, même état initial | Mêmes résultats et mêmes traces d'événements |
| U12 | Jonction atteinte par différentes routes | État de sortie préserve tous les faits non explicitement modifiés |

**Test métamorphique suggéré :** deux historiques qui ne diffèrent que par un fait **sans rapport** avec le bal doivent produire la même sélection de variantes pertinentes ; deux historiques qui diffèrent par une trahison importante ne doivent **pas** donner un dialogue entièrement identique si la relation est centrale.

## 7. Sorties attendues du futur outil

- Graphe des scènes principales et couche séparée des fils.
- Une trace A/B/C annotée avec `event_id`, `scene_id`, choix et état avant/après.
- Une vue « Pourquoi cette réplique ? » avec les conditions qui ont permis de l'exécuter.
- Une alerte lisible : `JOIN_BAL_2100: la variante Ren chaleureux est accessible avec ren_trust=0 dans l'historique B` (exemple de **bug volontaire à injecter**, non constaté).
- Un mini-rapport HTML de vérification, incluant **limites et couverture réelle**.
- Deux scènes visibles sur le moteur choisi, différentes malgré une même jonction, avec parcours témoin exportable.

## 8. Le point éditorial à préserver

Une **convergence structurelle** n'est pas une **convergence émotionnelle**. Le bal peut exister dans tous les parcours, mais Ren n'accueille pas le protagoniste de la même façon après une trahison ; une révélation horrifique peut même transformer la signification d'une scène romantique auparavant anodine. **Les choix importants doivent laisser des traces.**

Cet exemple n'est qu'un **étalon de comparaison à coder et playtester plus tard** ; il n'a pas été simulé ni évalué par une IA narrative réelle.
