# One Minute Empire — une décision par jour, 90 jours pour bâtir un empire

**Statut : idée retenue pour incubation, non démarrée.** Concept proposé puis développé dans un échange ChatGPT du 12 novembre 2026 ; le propriétaire a explicitement demandé son ajout dans `projects-incubator`. Aucune implémentation ni test utilisateur n'est revendiqué.

## Pitch

Jeu de gestion et de stratégie minimaliste : diriger une civilisation sur **90 jours réels**, à raison d'**une seule décision significative toutes les 24 heures**. Une session doit pouvoir tenir en environ une minute. Entre deux décisions, le monde continue de vivre et les choix anciens produisent des conséquences différées, parfois inattendues mais causalement compréhensibles.

**Promesse :** ne pas optimiser des dizaines de ressources chaque jour, mais assumer l'histoire irréversible d'une civilisation.

## Boucle de jeu envisagée

1. Lire un court bilan du jour (population, ressources, stabilité, événements, traces des choix antérieurs).
2. Examiner un dilemme contextualisé avec environ trois options et des conséquences partielles connues.
3. Valider **une décision unique** : aucun retour arrière, pas de décision supplémentaire payante.
4. Laisser le monde évoluer pendant les 24 heures suivantes : production, conflits, diplomatie, recherche, événements et conséquences en attente.
5. Revenir pour découvrir les résultats, les effets secondaires et le dilemme suivant.

**Exemple :** au jour 14, une sécheresse impose d'importer de la nourriture, de rationner les réserves ou de creuser un canal. Le canal peut préserver les récoltes au jour 35, puis provoquer un litige territorial au jour 58. Ce sont des exemples narratifs, pas des règles déjà équilibrées.

## Progression narrative possible (à ajuster)

- **Jours 1–15 :** fondation, survie, agriculture et lois.
- **Jours 16–30 :** expansion, villes, échanges, exploration.
- **Jours 31–50 :** puissance, diplomatie, inventions et crises politiques.
- **Jours 51–75 :** âge impérial, grands projets, guerres ou réformes.
- **Jours 76–90 :** héritage, derniers arbitrages et conclusion.

Au terme de la campagne : chronique générée à partir des événements effectivement simulés, portrait politique et culturel de l'empire, décisions charnières, réussites, échecs et épilogue. Une civilisation peut connaître la prospérité, la stagnation, une fragmentation ou une chute avant le jour 90 ; les issues exactes restent à concevoir.

## Piliers de design

- **Choix rares, conséquences profondes :** priorité à la causalité, aux arbitrages et aux retombées à long terme.
- **Monde autonome :** l'économie, les habitants, factions, voisins et événements évoluent entre deux connexions selon des règles compréhensibles.
- **Identité émergente :** décisions successives orientent l'empire vers le commerce, la science, le militarisme, la démocratie, etc., sans arbres de spécialisation rigides.
- **Irréversibilité loyale :** pas de rechargement immédiat ni d'achat de décisions ; les risques importants doivent être suffisamment lisibles pour éviter l'arbitraire.
- **Faible charge mentale :** bilan court, 3 options lisibles, écran principal évitant la microgestion et les notifications intrusives.
- **Variété rejouable :** événements contextualisés, chaînes de causes, biographies historiques et fins différentes.

## Pistes d'extension, hors MVP

- **Diplomatie asynchrone :** des empires d'autres joueurs proposent des traités, échangent ou entrent en conflit ; chaque participant consacre sa décision du jour aux engagements qui le concernent. Aucun PvP fondé sur le temps de connexion ou l'achat de tours.
- **« Échos de l'Histoire » :** après une campagne, des ruines, légendes, institutions ou technologies peuvent réapparaître comme traces limitées dans les nouvelles parties d'autres joueurs.
- **Campagnes et thèmes historiques/fantastiques alternatifs**, esthétique d'une carte évolutive, collection de chroniques.

Les systèmes multijoueurs, la persistance globale et les interactions entre campagnes introduisent des problèmes majeurs d'équilibrage et de modération ; ils ne sont **pas** des conditions du lancement.

## MVP possible (cadrage, pas développement engagé)

- **Plateforme :** navigateur mobile / PWA, solo d'abord.
- **Durée :** campagne prototype raccourcie pour tester rapidement la boucle, puis cible de 90 jours si la rétention le justifie.
- **Interactions :** exactement une décision par cycle de 24 h ; mode de simulation accélérée réservé aux tests.
- **État :** cinq indicateurs principaux au maximum ; relations entre quelques factions et mémoire des décisions.
- **Contenu :** viser un catalogue d'environ 100–150 événements **à terme** ; commencer avec un ensemble plus réduit de chaînes causales jouables de bout en bout.
- **Simulation :** moteur de règles déterministe ou pseudo-aléatoire à graine, événements différés, journal causal, sauvegarde et reprise. Aucune dépendance obligatoire à une IA générative.
- **Présentation :** écran du jour, trois options, carte 2D illustrative évolutive, frise des événements, chronique finale.
- **Économie :** pas de paiement pour obtenir davantage de décisions. Les cosmétiques et campagnes alternatives restent de simples hypothèses à évaluer.

## Risques et hypothèses à tester

1. **Rétention :** une seule minute quotidienne doit offrir assez de surprise et d'attachement ; éviter les journées creuses et le FOMO punitif.
2. **Agence réelle :** prouver que les décisions influencent les issues, et pas seulement les textes affichés.
3. **Lisibilité de la causalité :** rappeler pourquoi une crise se produit des semaines après une décision, sans tout révéler à l'avance.
4. **Équilibrage :** éviter une stratégie dominante et garantir des issues intéressantes même en situation d'échec.
5. **Horloge et abandon :** définir l'heure de réinitialisation, le sort d'un jour manqué, les fuseaux horaires et l'éventuel rattrapage sans « décisions stockées ».
6. **Contenu :** coût de rédaction de chaînes d'événements cohérentes et combinatoires, variété sans incohérence.
7. **Valeur économique :** monétisation non intrusive à démontrer ; aucune validation commerciale à ce stade.

## Frontières avec les projets existants

**Distinct de [Idle: Don't Play](idle-dont-play.md)** : celui-ci récompense volontairement une absence prolongée et une progression passive potentiellement sans plafond. One Minute Empire, lui, est une **stratégie narrative à cadence quotidienne contrainte**, où la ressource rare est le pouvoir de décision et non le temps d'absence.

Ce document reste une **fiche d'idée non démarrée**. Au démarrage d'un prototype ou d'un dépôt dédié, transférer le cadrage vers ce dépôt et retirer la fiche de l'index actif de l'incubateur selon la règle du projet.
