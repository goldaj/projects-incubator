# Contexte ChatGPT pour Projects Incubator

**Initialisé le 2026-10-24. Couverture : partielle, sauf les sources originales référencées explicitement.** Codex doit lire ce fichier après `AGENTS.md` et avant toute reprise du projet. Une mémoire reconstruite n'est pas la totalité du chat.

## Projet confirmé par le dépôt
- Dépôt : `goldaj/projects-incubator`.
- Objet actuel : index public uniquement des idées non démarrées.
- Contraintes : Ne jamais qualifier une idée de produit livré. Lier aux dépôts autonomes au lieu de dupliquer le code. Ne pas publier manuscrits inédits, données de trading, clés, secrets, historiques personnels ou configurations internes.
- Validation : Valider les liens et le classement des dossiers à chaque ajout ; aucune commande de build générale.

## Échanges attestés ou sources à lire

2026-10-18 14:05:48 UTC — Utilisateur, résumé reconstruit, non verbatim : rendre `projects-incubator` public et ne pas remplir les dépôts avec de simples coquilles ; privilégier vrais assets, sources et README.

2026-10-18 13:24:13 UTC — Utilisateur (verbatim, extrait) : « N'écrase aucun repo existant. »

2026-10-24 — Utilisateur (verbatim, heure non vérifiable) : « je te demande de lire mes repo git où tu es le dernier utilisateur, de rajouter un AGENTS.md pertinent s'il n'y en a pas. Mais en plus, tu rajoutera un document repérable par codex (peut être le référencer dans le AGENTS.md justement ?) où tu mets l'intégralité de nos échanges liés à ce projet. Mes questions, tes réponses (de sorte à les différencier) et les horodatages si tu les as. »

## Limites de couverture, fidélité et mise à jour
- Les passages marqués `verbatim` sont des extraits exacts disponibles dans le contexte ; les résumés ne doivent **jamais** être cités comme du dialogue mot pour mot. Aucune réponse complète de l'assistant n'a été inventée.
- Pour obtenir l'intégralité des questions, réponses et horodatages : intégrer un export authentique des conversations pertinentes ; conserver l'ordre et le rôle des messages, et expurger avant publication les éléments sensibles et hors projet.
- En intervention future, ajouter en bas les nouveaux dialogues sourcés et les décisions vérifiées, sans effacer les entrées précédentes. Ce journal et `AGENTS.md` sont versionnés dans Git.

## 2026-10-26 — Laboratoire de sociétés d'agents génératifs (conversation courante)

**Utilisateur (verbatim, premier message ; heure non attestée) :**
> tu vois le sujet de l'expérience concernée par cette vidéo youtube ?
> [https://www.youtube.com/watch?v=jRBUHrusAyk](https://www.youtube.com/watch?v=jRBUHrusAyk)
> Est-ce que tu peux me résumer le contexte et les enjeux succintement ?
> Est-ce que tu sais s'il existe un repo public pour reproduire l'expérience ?

**Assistant (résumé reconstruit, non verbatim) :** identification de Smallville/Generative Agents (2023), Project Sid et de travaux distincts sur les agents simulant des réponses humaines ; renvoi au code Stanford et à ses limites.

**Utilisateur (verbatim, demande d'ajout au dépôt ; heure non attestée) :**
> rajoute une entrée dans le repo du project incubator qui va dans le sens de la réalisation de ce projet, en poussant un peu plus loin la réfléxion scientifique et ce qu'on peut faire avec les IA d'aujourd'hui ; sur une machine modeste, puis sur une machine plus grosse (dite de "professionnel")

**Assistant (résumé reconstruit, non verbatim) :** cadrage d'un programme de recherche multi-agents. Nouvelle fiche [laboratoire-societes-agents-generatifs](../ia-et-multimedia/laboratoire-societes-agents-generatifs.md) : hypothèses falsifiables, ablations mémoire/réflexion, validité sociale, rumeurs, contraintes, modèles ouverts locaux et station professionnelle, architecture hybride et étapes P0–P6. Aucune simulation ni aucun benchmark matériel exécuté.

**Fidélité :** les textes Utilisateur ci-dessus viennent de la conversation accessible ; les résumés Assistant ne prétendent pas être une transcription intégrale. Heure exacte non attestée. L'historique des anciens chats reste partiel.


## 2026-10-26 — L'incubateur ne conserve que les idées non démarrées

**Utilisateur (verbatim, heure précise non attestée) :**
> Au fait, est-ce qu'il y a des choses dans l'incubator qui existent déjà sous forme d'un repo git dédié au projet ?
> L'incubator ne doit contenir que les projets qui n'ont pas démarré, une sorte d'index des idées.
>
> Tu peux me supprimer de l'incubator les idées qui sont déjà en cours sur des repo git dédiés dans mon github ? Ca me permettra de voir ce qu'il reste réellement à démarrer.

**Assistant (résumé reconstruit, non verbatim) :** audit croisé du catalogue et des dépôts accessibles. Retrait des fiches de développements, recherches engagées, prototypes, archives d'apprentissage et manuscrits en travail déjà hébergés dans Git. Nettoyage des index ; aucun dépôt de projet externe n'est supprimé. Les idées voisines mais indépendantes restent si elles n'ont pas démarré.

**Règle durable :** le catalogue est uniquement un index de futurs projets, pas un annuaire des dépôts actifs. Une fiche est retirée dès qu'un travail de projet est engagé dans un dépôt, même si le livrable se limite à une fondation de recherche. L'historique Git garde la trace des anciennes fiches ; les décisions antérieures dans ce journal restent des documents historiques.

## 2026-10-26 — Sortie de l'idée « Filtre AR Japon »
- L'utilisateur a créé le dépôt public autonome [japan-architecture-ar](https://github.com/goldaj/japan-architecture-ar), puis a demandé un plan d'attaque, une structure documentée et le démarrage du code.
- ChatGPT a créé `develop` pour la documentation de cadrage et une PR en brouillon [#1](https://github.com/goldaj/japan-architecture-ar/pull/1) pour un prototype local sur photographie. Ce prototype n'est ni une Lens Snapchat complète ni un système de suivi spatial.
- La fiche `ia-et-multimedia/assistant-ar-japan-snapchat.md` et son lien de navigation sont supprimés sur la présente branche de nettoyage; leur ancien contenu reste accessible dans l'historique Git.
- Source : conversation courante du 2026-10-26 (verbatim complet et horaire de chaque message non archivés ici), dépôt et PR effectivement vérifiés. La source de vérité du projet est désormais le dépôt autonome; l'incubateur ne conserve que les idées non démarrées.
