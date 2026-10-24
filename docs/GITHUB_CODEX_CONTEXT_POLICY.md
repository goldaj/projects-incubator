# Convention permanente : passation ChatGPT / Codex pour les dépôts Git

Créée à la demande du propriétaire le 2026-10-24.

## Portée
Pour tout dépôt Git où ChatGPT intervient désormais à la création ou à la modification, vérifier la présence d'un `AGENTS.md` à la racine et d'une archive accessible à Codex, idéalement `docs/CHATGPT_PROJECT_HISTORY.md`. Appliquer les règles propres au dépôt en priorité.

## Exigences
1. Lire les fichiers du projet et l'historique existant avant de travailler. Ne jamais écraser un dépôt ou fichier existant par simplification.
2. Si `AGENTS.md` est absent, le créer avec les objectifs, contraintes techniques, vérifications et liens vers le contexte. S'il existe, respecter ses règles et ajouter seulement un lien si nécessaire.
3. Conserver dans `docs/CHATGPT_PROJECT_HISTORY.md` les discussions de projet disponibles, en distinguant les messages `Utilisateur` et `Assistant`, avec dates et fuseau horaire attestés. `Verbatim` exclusivement si le texte exact est connu. Utiliser `Résumé reconstruit (non verbatim)` dans les autres cas.
4. Si des séances anciennes sont indisponibles, **écrire explicitement que l'historique est incomplet**. Ne pas imaginer des messages ni des dates. Demander ou exploiter un export fidèle des conversations quand il est disponible.
5. Lors de chaque modification ultérieure, enrichir l'archive des échanges réellement disponibles et consigner les nouveaux choix de produit/architecture. Conserver l'historique versionné.
6. Sécurité et confidentialité : ne publier ni mots de passe, tokens, clés, données personnelles, notes de comptes privés, manuscrits inédits, ni contenus sans droits. Les documents de contexte doivent respecter la visibilité et les règles de confidentialité du dépôt.
7. Vérifier après les modifications que les liens et fichiers existent sur la branche voulue, et rapporter les exceptions honnêtement.

## Limites de cette convention
Ce fichier est une règle Git lisible par Codex lorsqu'il consulte le dépôt, pas une preuve que tous les assistants futurs auront un accès automatique à l'ensemble de l'historique ChatGPT ni que leur mémoire globale sera modifiée. Elle ne remplace pas les consignes particulières de chaque dépôt.
