# AniCompass — découvrir quoi regarder ou lire ensuite

**Statut : idée non démarrée.** Enrichissement 2026-10-26. Le nom et la famille fonctionnelle viennent d'une proposition de septembre 2026 ; ce document décrit une interprétation de produit.

## Problème
Les recommandations d'anime/manga/light novel sont souvent basées sur quelques étiquettes (« romance », « action ») et oublient **pourquoi** une personne a aimé une œuvre, ce qu'elle a déjà terminé ou abandonné et **son envie du moment**.

## Expérience cible
Une personne choisit le média (anime, manga, light novel), signale quelques œuvres de référence et exprime son humeur : romance avec progression avant la mise en couple, protagoniste masculin, réalisme ou surnaturel, série déjà achevée ou longue, jalousie/drama, etc. L'outil propose une petite sélection **expliquée**, avec les incompatibilités affichées.

Scénario : « J'ai envie d'une romance humaine, longue et déjà terminée, avec de la tension avant le couple. Évite mes titres lus et abandonnés. » Le moteur doit pouvoir répondre « aucun résultat solide » plutôt que réinventer un catalogue.

## Concepts fonctionnels
- **Profil explicite et révisable** : goûts durables, exclusions, envies temporaires, media préféré.
- **Catalogue externe licencié / sourcé** : titre original, traduction, formats, statut de publication, chapitre/volume, tags et synopsis ; liens vers les sources.
- **Matching multi-critères** : filtres bloquants séparés des préférences pondérées ; explication du score (« satisfait X, incertain sur Y »).
- **Découverte et diversité** : éviter de proposer dix fois le même archétype ; gérer des propositions audacieuses mais justifiées.
- **Feedback** : aimé, déjà lu, abandonné, à garder pour plus tard, faux positif ; distinguer note de l'œuvre et adéquation à l'humeur.
- **Incertitudes honnêtes** : certains tags fins ne sont pas dans les bases de données et exigent une vérification humaine.

## MVP envisagé
Prototype local avec **données publiques et quelques titres fictifs/autorisé**, filtres stricts, score explicable, recommandations et export. Comparer moteur par règles à éventuel reranking LLM ; celui-ci ne doit inventer ni statut de série ni synopsis. Pas de scraping massif, pas de publication de l'historique personnel de l'utilisateur.

## Frontière avec Media Backlog
**AniCompass recommande et justifie** ; **Media Backlog suit et organise**. L'intégration future est possible, mais chaque idée doit démontrer une valeur indépendante.

## Recherche et critères de succès
Vérifier fournisseurs/licences des métadonnées, fréquence de mise à jour et disponibilité des formats. Évaluer sur des requêtes où les contraintes sont explicites : taux de violation des exclusions, part de recommandations déjà connues, utilité des justifications, couverture réelle. Ne pas appeler un modèle IA avant qu'un baseline déterministe ait été évalué.

**Non acté :** plateforme, source de données définitive, moteur de classement et personnalisation avancée.
