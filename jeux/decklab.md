# DeckLab — concevoir et équilibrer un deckbuilder

**Statut : idée non démarrée.** Cadrage enrichi le 2026-10-26 à partir d'une proposition de septembre 2026. L'idée originale évoquait un éditeur de cartes et un **simulateur statistique pour deckbuilder roguelite**.

## Pourquoi faire ce projet ?
Dans un jeu de cartes à construction de deck, deux cartes qui paraissent équivalentes isolément peuvent créer des stratégies disproportionnées lorsqu'elles se combinent. Le but envisagé est de détecter **déséquilibres, combos dominants et stratégies inutiles** avant de développer tout un jeu.

## Cas d'usage
Un game designer crée des cartes : coût, rareté, tags, effets, conditions de déclenchement. Il configure un deck, quelques ennemis/rencontres fictifs et les règles de tour. Il lance 1 000 simulations avec des seeds différentes pour comparer une version A et une version B des règles. Le tableau indique taux de victoire, durée, pioche, dégâts/ressources et distribution des résultats. Il peut ensuite expliquer **quel changement** a provoqué un écart plutôt que s'en tenir à l'intuition.

## Modules envisagés
- **Schéma de cartes** : identifiants, propriétés, descriptions et effets structurés, avec validation.
- **Moteur déterministe** : transitions d'état, pile/résolution d'effets, ordre d'action et générateur aléatoire seedé.
- **Simulateur** : plusieurs stratégies de joueur, de la plus simple à une politique d'agent ; comparaison équitable à seeds identiques.
- **Mesures** : équilibre par archétype, sensibilité aux tirages, cas extrêmes, cartes sur/sous-jouées, coût de calcul.
- **Atelier** : édition, import/export JSON, replay d'une partie synthétique, tableaux des écarts entre deux versions.

## MVP de recherche
Une dizaine de cartes inventées, un adversaire simple, des règles très réduites, deux stratégies déterministes, simulations batch et export JSON/CSV. Inclure des tests prouvant l'invariance des règles et la répétabilité à seed donné. **Ne pas commencer par une interface de jeu jouable**, de l'animation ou un contenu commercial complet.

## À mettre à l'épreuve
Le score « taux de victoire » seul ne suffit pas : une méta variée et agréable compte aussi ; les stratégies d'agents biaisent les résultats. Définir des métriques d'équilibrage robustes, rechercher les références de simulateurs de deckbuilders et vérifier si l'outil serait générique ou lié à un futur jeu.

**Non acté :** inspiration de jeux précis, grammaire d'effets, moteur visuel, monétisation ou existence d'un jeu associé.
