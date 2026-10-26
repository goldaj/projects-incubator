# Idle: Don't Play — le jeu qui récompense l'absence

**Statut : concept de jeu non démarré.** Distinct de [idle-clicker-tkinter](https://github.com/goldaj/idle-clicker-tkinter), où l'interaction et l'achat améliorent la progression : ici, **jouer nuit à la stratégie optimale**.

## Vision, règle paradoxale
Un jeu idle dans lequel **moins l'on ouvre l'application, plus la progression est avantageuse**. Le joueur peut s'absenter aussi longtemps qu'il veut : **aucun plafond d'accumulation des gains** imposé par design. Le but méta est de « ne pas jouer » ; paradoxalement, il faut rendre le retour rare intéressant.

## Règles à explorer
- Production passive continue en fonction du temps écoulé, avec bonus de patience croissant selon la durée **ininterrompue d'absence**.
- Aucune jauge qui se remplit et bloque les gains après 8 ou 24 heures. Éventuellement **effet composé** dont la stabilité mathématique doit être contrôlée.
- Ouvrir le jeu peut interrompre ou réduire le multiplicateur d'abstinence ; le coût du retour doit être annoncé, pas piéger le joueur.
- Au retour : récit de ce que l'univers a accompli en son absence, nouvelles découvertes, choix de long terme, puis repartir pour plusieurs jours.
- Possibilité de refuser les notifications, puisqu'un jeu qui supplie qu'on revienne détruirait son propre concept.

## Challenge fondamental : le temps et la confiance
- Quel temps prendre comme référence si l'appareil est hors ligne ? L'heure locale est manipulable. Prototype offline avec simulation déterministe ; horloge serveur uniquement si classement/économie en ligne le justifie.
- Stocker un état compact (`derniere_interaction`, `production_rate`, `regles_version`), calculer `delta_t` lors du retour, **sans boucle simulant chaque seconde**.
- Grandes durées et exponentielles : utiliser nombres à grande amplitude / logarithmes / notation scientifique ; tester overflow et invariants de croissance.
- Un « bonus infini » est une **absence de plafond temporel**, pas l'infini numérique pour un temps fini. Économie doit demeurer interprétable.

## MVP
Prototype navigateur ou bureau minimal ; une ressource, une règle de gain différé, quatre paliers temporels, un événement narratif au retour, sauvegarde locale, aucune microtransaction. Tests simulant absence de 1 h, 1 jour, 1 mois, 10 ans ; mesurer cohérence des nombres et plaisir du retour.

## Hypothèses à mesurer
Expérience « check compulsif » contre « revenir une fois par semaine », satisfaction à la progression passive, effet de multiples sessions, abus changement d'horloge, sentiment d'un choix significatif au retour. Pas de course FOMO ou mécanisme punitif caché.

## Questions ouvertes
Est-ce un jeu satirique avec un écran « ne cliquez pas » ou une vraie économie d'exploration ? Le bonus d'absence doit-il être **strictement croissant** à tout instant, ou seulement le rendement global ? Une fin atteignable existe-t-elle ?
