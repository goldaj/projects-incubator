# Chess Cosmetics — jeu d'échecs à collection de skins gacha

**Statut : idée à démarrer.** Jeu d'échecs classique avec collection d'habillages cosmétiques tirés aléatoirement. **Distinct de [chess-roguelite](https://github.com/goldaj/chess-roguelite)** : ce projet conserve les règles orthodoxes et ne contient ni pouvoir de pièces ni progression de combat roguelite.

## Concept
Jouer aux échecs avec des ensembles visuels thématiques de pièces, plateaux, effets et animations. Obtenir des skins via un système de **gacha** avec rareté affichée. Le plaisir provient d'une expérience d'échecs agréable et d'une collection esthétique, **jamais d'un avantage compétitif acheté**.

## Expérience cœur
- Jeu local à deux ou contre un moteur libre, règles standard (échec, roque, prise en passant, promotions, répétition, nulle).
- Collection de skins par pièce, famille cohérente (fantasy, pixel-art, minimalisme, rétro), prévisualisation sur plateau et configuration individuelle.
- Ouverture de « capsules » / paquets avec animation facultative, historique, raretés et prévisualisation des probabilités.
- Collection, doublons, conversion en fragments, objectif de compléter une série.
- Cosmétiques lisibles en partie : silhouettes reconnaissables, mode contraste et pièces standard disponibles gratuitement.

## MVP à faible risque
Échiquier local, moteur de règles existant et testé, **12 à 24 skins** en illustrations simples, packs gagnés **par jeu et non par argent**, tirage pseudo-aléatoire vérifiable et sauvegarde locale. Pas de comptes, mode multijoueur en ligne ni paiement réel initialement.

## Monétisation à challenger avant tout code payant
Le gacha avec achats d'argent réel implique risques juridiques (règles jeux de hasard et consommation), mineurs, économie de prédation et interfaces manipulatrices. Pour la première étude, **tester la rétention et la collection en monnaie fictive gratuite**, sans argent réel ; si le modèle payant est retenu, analyser les règles applicables, plafonds, transparence des probabilités, vérification d'âge et possibilité d'achat direct de skins. Ne jamais dissimuler les taux de tirage.

## Architecture candidate
Moteur de règles d'échecs éprouvé + UI indépendante ; données de skins sous manifestes versionnés avec licences ; algorithme de loot box isolé avec taux configurables et **tests statistiques** ; inventaire et transactions locales idempotentes, migrations de sauvegarde.

## Mesures de validation
Reconnaissance des pièces pendant une partie, attrait de la collection, équilibre des raretés, risque de frustration, temps pour obtenir une série, nombre de doublons, stabilité des sauvegardes ; la qualité du jeu d'échecs doit rester indépendante des skins.

## Inconnues
Web ou mobile ? Matchmaking réel un jour ? Une seule collection de pièces à acheter ou skins par pièce ? Paiements réels souhaités ou cosmétiques collectables uniquement ? Les possibilités payantes sont **différées**.
