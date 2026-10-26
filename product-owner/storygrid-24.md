# StoryGrid 24 — tableau de contraintes pour récit illustré

**Statut dans cet incubateur : périmètre autonome à revalider.** Cadrage reconstitué le 2026-10-26. Attention au possible recouvrement avec un **projet déjà engagé**.

## Origine retrouvée
Une proposition de septembre 2026 associait explicitement StoryGrid 24 à la préparation de l'histoire illustrée **Le garçon et la libellule**. La proposition mentionnait un récit sur **24 pages**, une liste de **24 mots imposés**, l'ordre et l'unicité de ces mots, des mots initiaux pouvant former des messages, deux scénarios « Minibelle », des pages où le garçon écrit, les illustrations et la cohérence d'un arc en trois actes. Ces éléments sont le **contexte historique de la proposition**, pas la permission de publier le manuscrit ni un nouvel ensemble de contraintes validées ici.

L'utilisateur a ensuite indiqué que StoryGrid 24 pouvait relever d'un **projet déjà en cours**. Le dépôt `goldaj/le-garcon-et-la-libellule` existe : cette fiche ne doit **pas** servir de deuxième dépôt pour développer le même travail.

## Intuition fonctionnelle
Représenter chaque page par une ligne d'une grille avec : rôle narratif, scène, personnages, émotion, texte, mot-clef contraint, indices cachés, illustration et statut de validation. Les liens entre pages permettraient de repérer ce qu'une relecture à plat oublie.

### Exemple de contrôle
Si une contrainte prévoit un mot unique par page, le vérificateur identifie un doublon ou une page sans mot. Si une énigme emploie la première lettre de chaque page, il reconstitue le message et signale les écarts. Il **ne prétend pas** juger automatiquement la qualité littéraire.

## Deux périmètres possibles à ne pas confondre
- **Outil générique futur** : grille réutilisable pour des récits illustrés de longueurs variées, tests de contraintes paramétrables et exports locaux.
- **Fonction du projet existant** : vérificateur spécifique à *Le garçon et la libellule*. Dans ce cas, les travaux et la documentation appartiennent **à ce dépôt**, et cette entrée doit disparaître.

## Questions et protocole avant décision
Vérifier si le dépôt existant couvre déjà cet usage et si l'utilisateur veut réellement un logiciel générique indépendant. Si oui, concevoir un petit schéma de 4 pages **entièrement fictives**, des contraintes configurables et des tests de détection des violations. Ne jamais publier les vrais textes, rebondissements, fichiers sources ou illustrations du livre dans cet index public.

**Point non résolu :** autonomie réelle de cette idée. Ne pas lancer un prototype ici tant que la distinction n'est pas établie.
