# Deep Tech Watch — laboratoire de veille scientifique et financière

**Statut : idée d'outil autonome à démarrer.** Documentation enrichie le 2026-10-26 à partir des demandes de veille de septembre et octobre 2026. Les rapports ChatGPT déjà planifiés **ne constituent pas** une implémentation de ce logiciel.

## Vision et motivation attestées
Suivre les technologies de rupture en croisant **avancées scientifiques et techniques, entreprises concernées, investissement possible et risques**. L'angle financier est prioritaire, mais les conclusions doivent être fondées sur des faits techniques. Domaines explicitement suivis : **informatique quantique, fusion nucléaire, technologies spatiales**, plus **transports atypiques / dirigeables et technologies anciennes revisitées** dans un autre volet de veille.

Les demandes existantes ont évolué vers un **rapport deep tech mensuel consolidé**, comprenant des sections approfondies sur le quantique, la fusion et le spatial. La cadence d'une future application n'est pas fixée par le planning ChatGPT existant.

## Cas d'usage
Un utilisateur lit « une entreprise annonce un réacteur à fusion révolutionnaire ». L'outil retrouve la source primaire, sépare la mesure obtenue de la promesse industrielle, identifie la maturité de la technologie, puis liste les acteurs exposés, leurs liens réels avec la technologie et les points à vérifier lors de la prochaine annonce. Le mois suivant, il signale **ce qui a objectivement changé**.

Pour le spatial, il doit notamment distinguer la société qui développe un lanceur, celle qui exploite des satellites, celle qui fournit des composants et celle qui n'a qu'une exposition marginale. Une entreprise « liée à l'espace » n'est pas nécessairement un pure player ni une exposition boursière directe.

## Objets de recherche à documenter
- **Quantique** : qubits physiques/logiques, correction d'erreurs, fidélité, portes, démonstrations réellement utiles, comparaison entre architectures.
- **Fusion** : bilan énergétique et périmètre de mesure, confinement, matériaux, calendrier industriel, financement, partenaires, reproductibilité.
- **Spatial** : technologies, cadence de lancement, revenus, carnet de commandes, marges, besoins de capitaux, dilution, contrats et crédibilité de l'exécution.
- **Dirigeables/transports atypiques** : cas d'usage, gains théoriques vs infrastructure, maturité, sécurité, économie complète et contraintes de certification.

## Fonctions d'un produit possible
1. **Collecter** des documents datés : publications, rapports, communiqués, dépôts réglementaires, informations financières fiables.
2. **Dédupliquer et relier** les annonces d'un même événement, y compris les corrections ultérieures.
3. **Qualifier la preuve** : annonce, prototype testé, publication évaluée, démonstration indépendante, déploiement commercial ; afficher le niveau de confiance.
4. **Construire des fiches de technologies et d'acteurs** avec jalons chronologiques, verrous, concurrents, risques, financements et catalyseurs.
5. **Cartographier l'exposition économique** : sociétés cotées ou privées, exposition directe ou indirecte, pure players, chaîne de fournisseurs, instruments accessibles, sans présenter l'accès boursier comme acquis.
6. **Produire un rapport différentiel** : nouveautés depuis l'édition précédente, changement des probabilités/hypothèses, perspectives bull/base/bear justifiées.
7. **Garder une bibliographie vérifiable**, une historique des corrections et la séparation stricte entre fait, hypothèse et opinion.

## MVP étudiable
Se limiter à **un domaine**, une vingtaine de sources autorisées, une dizaine d'acteurs et un mois d'annonces. Générer deux versions du rapport à une semaine d'intervalle, en indiquant précisément les changements. Réaliser une revue humaine d'un échantillon pour mesurer citations erronées, doublons, fausses attributions et confiance abusive. L'IA peut aider à la synthèse, mais ne doit jamais être traitée comme source primaire.

## Frontières et risques
Ce produit **n'est ni un bot de trading ni un moteur de recommandations d'achat automatiques**. Une découverte scientifique majeure peut ne rien rapporter à l'action liée, et une valorisation attractive ne prouve aucune rupture technologique. Les chiffres boursiers, IPO, tickers et disponibilités de courtage sont temporels et doivent être revérifiés au moment du rapport.

**Questions encore ouvertes :** produit personnel ou publiable, acquisition des données, coûts d'accès, diffusion par email ou dashboard, fréquence de collecte. Ne pas dupliquer une automatisation déjà en service avant de démontrer l'intérêt d'un outil séparé.
