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


## 2026-10-26 — Toile AR planétaire persistante (idée non démarrée)

**Utilisateur (verbatim, message intégral accessible dans la conversation courante ; heure exacte non attestée) :**
> on va créer une nouvelle entrée dans l'incubator sur git.
> Il s'agit d'un projet de réalité mixte.
>
> Le cas d'usage :
> On mets des lunettes AR/réalité mixte ou une simple appli sur le téléphone.
> On voit le monde réel. Par contre on peut "peindre" dessus, rajouter des lignes et écrire simplement.
> Par contre, les lignes peintes sont localisées au plus précis possible. Geolocalisée, avec la hauteur prise en compte. Et son persistentes pour TOUT LE MONDE qui utilise l'application.
> C'est literralement la planète entière qui devient le tableau. On démarrera par une toute petite zone parce que je pense que la grosse difficulté ici sera la quantité de mémoire à enregistrer et charger en tant réel quand la personne arrive à proximité d'une nouvelle ligne peinte.
>
> Il faudra étudier si des projets similaires existent, la faisabilité, les conditions et le matériel nécessaire, mais aussi l'architecture, l'infra, l'algorithme et tout le nécessaire en tant que chercheur avant d'envoyer l'ingénieur réfléchir au code directement.

**Assistant (résumé reconstruit, non verbatim) :**
- A identifié et parcouru les consignes du dépôt public : l'incubateur n'accueille que les idées sans recherche ni développement engagé dans un dépôt autonome.
- A conduit un premier repérage **documentaire uniquement** de projets comparables (WallaMe, Kanvio, Spray, Cospray), moteurs de localisation (ARCore Geospatial, Niantic Spatial VPS, Apple ARKit GeoTracking), standards (OGC GeoPose / 3D Tiles) et indexation spatiale (H3 / PostGIS).
- A caractérisé séparément trois difficultés : stockage mondial des traits, recalage visuel spatial précis entre appareils/sessions, hauteur et surfaces 3D ; a conclu qu'aucune précision centimétrique mondiale ne peut être promise d'après ce repérage.
- A créé [la fiche de cadrage scientifique Toile AR planétaire persistante](../ia-et-multimedia/toile-ar-planetaire-persistante.md) avec critères de falsification, hypothèses, modèle conceptuel, architecture candidate, stratégie de cache et protocole P0–P5, en vue d'une éventuelle recherche puis intervention de Codex plus tard.
- A ajouté la fiche à l'index `ia-et-multimedia/README.md`. **Aucun code, benchmark ni test AR réel n'a été développé ou exécuté ; aucun nouveau dépôt projet n'a été créé.**

**Règle de reprise :** commencer par le comparatif étayé (P0) et la métrologie (P1), contester les choix de fournisseurs et les hypothèses de précision, puis transférer le dossier dans un dépôt dédié et supprimer l'entrée de l'incubateur lorsque le projet démarre effectivement. Les échanges antérieurs du compte non contenus dans ce journal ne sont pas implicitement retranscrits.

## 2026-10-26 — Passage de « dashboard Twitch » à produit autonome
- Le propriétaire a créé https://github.com/goldaj/twitch-streamer-dashboard et précisé le premier produit réellement prioritaire : voyant discret vert/orange/rouge en temps réel indiquant état Twitch, image reçue et audio côté spectateur. Normalisation automatique du volume réglable par streamer mise au backlog pour plus tard.
- Le projet autonome contient des recherches, consignes Codex et un prototype simulé sur [PR #1](https://github.com/goldaj/twitch-streamer-dashboard/pull/1). **Ce code simulé ne détecte pas encore des pannes Twitch réelles.**
- La fiche de l'incubateur et sa ligne de navigation sont retirées en PR sans fusion; l'ancien texte reste dans l'historique Git.
- Source : conversation visible du 2026-10-26, heure précise des messages non attestée. Pas de transcription complète des échanges plus anciens.

## 2026-10-26 — Consolidation des idées VTuber Live2D
- Le nouveau dépôt public https://github.com/goldaj/vtube-physics-lab réunit les idées de physique Live2D, d'AI Replay et de visualisation mobile autonome. PR technique : https://github.com/goldaj/vtube-physics-lab/pull/1.
- Le propriétaire ajoute explicitement le besoin de vêtements 2D interchangeables avec adaptation automatique au mouvement et à la physique, sans rig manuel.
- La fiche `jeux/vtube-physics-lab.md` était déjà absente de main au moment de cette passe, avec son index mis à jour. La présente branche retire l'idée apparentée `ia-et-multimedia/live2d-remote-lab.md` et son index : le projet a démarré.
- Son ancien contenu, y compris les besoins d'audio distant et de fonctionnement sur téléphone hors Wi-Fi, a été recopié dans https://github.com/goldaj/vtube-physics-lab/blob/feat/replay-clothing-spike/docs/LEGACY_LIVE2D_REMOTE_LAB.md ; l'historique Git en conserve également la version antérieure.
- Les informations sur la conversation de septembre 2026 sont partielles et signalées comme telles; aucune transcription complète n'est inventée.


## 2026-10-26 — Déclassement volontaire de thèmes non retenus comme projets (conversation actuelle)

**Utilisateur (résumé fidèle, non verbatim ; heure exacte non attestée)** : les outils de suivi anime/manga/light novel avaient été proposés de bonne foi comme idées de logiciels, mais l'utilisateur choisit de les retirer de l'incubateur. Il demande aussi de supprimer la fiche de fiction « La sauvegarde impossible », tout en **conservant la catégorie « Créatif et écriture » vide et prête à accueillir de futurs projets**.

**Assistant (résumé des opérations vérifiées dans Git)** : suppression des fiches `anime-et-media/anicompass.md`, `anime-et-media/media-backlog.md`, de l'index `anime-et-media/README.md` (ce qui retire le répertoire du HEAD Git), et de `creatif-et-ecriture/la-sauvegarde-impossible.md`. Mise à jour de `creatif-et-ecriture/README.md` avec l'état « aucune idée » afin que Git conserve la catégorie. L'index racine n'affiche plus Anime et médias. L'historique Git garde ses anciennes versions.

**Règle produit ajoutée** : seules les idées **que le propriétaire veut effectivement garder comme futurs projets** appartiennent à l'incubateur. L'existence d'une conversation riche sur un thème ne suffit pas. La correction d'un classement antérieur ne signifie ni suppression des discussions d'origine ni jugement sur leur intérêt.

**État résiduel** : les projets PO ont disparu de main ; un fichier `finance-et-recherche/deep-tech-watch.md` reste présent malgré la demande antérieure de suppression du répertoire complet, sa suppression ayant été bloquée. Il n'est plus dans l'index. Aucun projet dédié n'a été trouvé parmi les dépôts GitHub accessibles pour `toile-ar-planetaire-persistante.md` ; cette idée reste dans l'incubateur.
