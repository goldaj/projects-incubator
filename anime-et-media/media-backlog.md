# Media Backlog — mémoire personnelle des œuvres

**Statut : idée non démarrée.** Enrichissement documentaire 2026-10-26. Concept proposé en septembre 2026.

## Besoin
Une personne navigue entre anime, mangas, light novels, romans et jeux. Elle peut oublier où elle s'est arrêtée, ce qu'elle a abandonné, et surtout **pourquoi** elle voulait reprendre une série. Des favoris et des notes isolées ne constituent pas une mémoire exploitable.

## Cas d'usage
Ajouter une œuvre, choisir un statut (« à découvrir », « en cours », « en pause », « terminé », « abandonné »), noter le dernier épisode/chapitre/volume, une appréciation, une raison de pause et éventuellement une date de reprise souhaitée. Retrouver en quelques secondes « mes mangas en pause », « séries terminées », « romances appréciées », sans dépendance à un compte externe.

## Modèle de données conceptuel
- **Œuvre** : titre principal, alias/titre original, formats liés (adaptation anime vs manga), source facultative.
- **Suivi par format** : statut, progression avec unité explicite, note personnelle, date de mise à jour.
- **Journal** : historique des changements, tags et notes de contexte.
- **Listes** : envie actuelle, favoris, suggestions à tenter, relire un jour.
- **Confidentialité** : données locales par défaut, sauvegarde/export et suppression totale ; synchronisation optionnelle à étudier seulement après un besoin identifié.

## MVP envisagé
Application légère utilisable sans connexion, CRUD, filtres rapides, recherche, import/export CSV/JSON et sauvegarde locale. Commencer avec des titres fictifs ; l'intégration de sources tierces et leurs conditions d'utilisation viendrait ensuite.

## Non-objectifs initiaux
Agrégation automatique de tout l'historique de visionnage, réseau social, commentaires publics, bibliothèque de fichiers piratés, collecte d'informations personnelles depuis des services externes.

## Différence avec AniCompass
Media Backlog est **la source de vérité sur ce qu'on a fait et veut faire**. AniCompass est **un moteur de découvertes**. Ne pas les fusionner par défaut, mais définir un modèle commun optionnel et éviter deux saisies contradictoires si les deux projets commencent.

## Questions pour valider le besoin
L'utilisateur préfère-t-il l'outil autonome, une extension d'un catalogue existant ou simplement un export ? Quel format de progression est pratique lorsqu'un titre possède plusieurs adaptations ? Comparer trois workflows sur un corpus fictif de 20 titres, noter les pertes de données et le nombre d'actions nécessaires.

**Non acté :** stockage définitif, comptes utilisateurs, intégration AniList/MAL, application web ou mobile.
