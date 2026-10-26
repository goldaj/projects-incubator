# Romance Multiverse — visual novel à routes et ambiances collectionnables

**Statut : idée de jeu non démarrée.** Jeu narratif à choix multiples centré sur la drague et la découverte de fins, mais surtout de **familles entières de routes** aux genres et tons inattendus.

## Promesse
Le joueur pense démarrer une romance, puis ses choix peuvent ouvrir une comédie absurde, un thriller, une histoire tendre, une enquête, une route horrifique, une histoire sensuelle entre adultes, une parodie ou une narration méta. **Découvrir un type de route inédit** procure autant de satisfaction que trouver l'une des nombreuses fins.

## Boucle du joueur
1. Entrer dans une situation commune avec personnages récurrents.
2. Choisir dialogues, actions, attitudes, lieux et secrets, avec conséquences durables.
3. Voir certains embranchements modifier **le genre narratif, l'ambiance, les règles de présentation et parfois le point de vue**.
4. Atteindre une fin, obtenir une vignette de collection et des indices non spoilants sur les branches non découvertes.
5. Rejouer avec raccourcis intelligents, nouveaux choix, carte partielle du parcours et mémoires de décisions.

## Système de collection
Trois dimensions : **fin**, **archétype de route** (romcom, amour tragique, horreur, comédie noire, polar, méta, etc.), **événement secret / variante de personnalité**. Collection lisible, taux d'exploration, indices progressifs et mode spoiler désactivé. Un système de « portes » conditionnées à plusieurs runs permet des routes inédites sans gonfler artificiellement la durée.

## Défis de conception
Explosion combinatoire des routes et scénarios : séparer variables d'état, arcs narratifs modulaires, scènes réutilisables à variations contextuelles et scènes uniques qui justifient la route. Éviter les faux choix sans conséquences. Tous les personnages engagés dans une romance explicite sont **adultes** ; définir avertissements et contrôle de contenu pour les branches sombres.

## MVP vertical slice
3 personnages adultes, 3 familles d'ambiance radicalement distinctes, 6 à 9 fins, 1 secret, 25–40 scènes et une collection de parcours. Test à l'aveugle : un joueur peut-il détecter des différences d'ambiance, comprendre ses choix et avoir envie de recommencer ?

## Architecture candidate
Moteur de visual novel éprouvé (Ren'Py ou Godot à comparer), contenu data-driven en scripts ou graphes, `flags` typés et conditions contrôlées, représentation statique du graphe, simulations automatiques de parcours, détecteur de fins inaccessibles, sauvegardes robustes et tests des conditions.

## Risques / critères de réussite
Coût énorme d'écriture, QA de branches, incohérences de personnage, changement de ton mal préparé, spoil de collection et rejouabilité répétitive. Mesurer chemins uniques atteignables, variété perçue, proportion de scènes inédites et cohérence des embranchements. Prévoir un outil interne de simulation de runs avant l'ambition « énormément ».

## Points à décider
Univers contemporain ou multivers ? Un protagoniste fixe ou personnalisé ? Jeu plutôt humour/romance, avec routes d'horreur rares, ou toutes les ambiances également importantes ? Génération IA assistée ou écriture humaine comme source de vérité ?
