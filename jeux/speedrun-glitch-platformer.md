# Glitch Runner — plateforme conçue pour le speedrun

**Statut : concept de jeu non démarré.** Plateformer dans lequel des **glitchs volontaires, maîtrisés et reproductibles** sont intégrés au design. Le joueur découvre des techniques d'apparence accidentelle à mesure qu'il progresse, puis les combine pour optimiser ses temps.

## Promesse de jeu
La « cassure » des règles fait partie du plaisir : traverser un bord de collision, conserver un élan, interagir bizarrement avec une plateforme mobile, faire un saut impossible. Chaque technique doit être **enseignée sans spoiler toutes ses applications**, puis réutilisable pour des records et raccourcis secrets.

## Progression
1. Niveau 1 : mouvement standard parfaitement lisible.
2. Découverte contrôlée d'un premier « glitch » et salle d'entraînement avec démonstration fantôme.
3. Niveaux à chemin normal et chemin speedrun, avec indices dans l'environnement.
4. Nouvelles techniques (momentum storage, corner clip, coyote-time extrême, reset de gravité, interaction de hitbox) ajoutées une par une.
5. Fin de campagne accessible sans exploiter tout ; médailles et routes secrètes réservées à la maîtrise combinée.
6. Mode chrono / ghost / replay : rejouer vite, parcourir les routes cachées, comparer des splits.

## Choix d'ingénierie décisif
Les « glitchs » doivent être des **mécaniques codées intentionnellement avec invariants**, pas des bugs dépendant du framerate, du matériel ou de comportements non déterministes. Simuler collision et mouvement à pas fixe, rejouabilité par inputs horodatés, seed et version du moteur. Une mise à jour ne doit pas casser les temps historiques.

## MVP vertical slice
Personnage 2D avec contrôles précis ; 4 salles ; 2 techniques distinctes et combinables ; chrono, reset instantané, ghosts locaux ; 3 routes par salle ; tests automatisés de trajectoires. Graphismes placeholders et musique provisoire.

## Questions de level design / R&D
- Un débutant comprend-il seul la première technique ?
- Combien de tentatives avant réussite ? Qu'est-ce qui distingue une technique exigeante d'un hasard ?
- Une séquence de mouvements peut-elle être reproduite à 30, 60 et 144 Hz ?
- Un joueur moyen termine-t-il la campagne sans connaître les shortcuts avancés ?
- La collection des routes vaut-elle mieux qu'un leaderboard en ligne initialement ?

## Architecture candidate
Godot 2D ou autre moteur comparé après prototype ; machine à états du personnage explicite ; graphe de niveaux ; enregistreur/rejoueur d'inputs ; suite de tests de replays « dorés » pour prévenir les régressions ; leaderboard online uniquement après mécanisme anti-triche.

## Risques
Glitchs illisibles, frustrants, trop faciles à spammer, leaderboard dominé par exploits **non voulus**, physics non déterministe et coût exponentiel du level design. Le prototype doit mesurer les réussites et la facilité d'apprentissage avant l'ajout de dizaines de techniques.

## Questions ouvertes
Direction humoristique ou hardcore ? Jeu PC clavier/manette d'abord ou mobile ? Glitchs révélés progressivement ou secret total avec indices ? Sessions de 1 minute ou niveaux longs ?
