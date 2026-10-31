# Contexte ChatGPT pour Projects Incubator

**Initialisé le 2026-10-24. Couverture : partielle, sauf les sources originales référencées explicitement.** Codex doit lire ce fichier après `AGENTS.md` et avant toute reprise du projet. Une mémoire reconstruite n'est pas la totalité du chat.

## État actuel confirmé — 31 octobre 2026

- Le catalogue compte **16 fiches actives** : IA et multimédia (5), recherche et innovation (1), outils logiciels et productivité (1), infrastructure et médias (1), communautés et échanges (1), finance et crypto (3), jeux (3), créatif et écriture (1). Ce total provient du relevé des fichiers de la branche principale, pas des décomptes historiques ci-dessous.
- Trois idées explicitement retenues ont été ajoutées : [RETRO-LAB](../recherche-et-innovation/retro-lab.md), [AUTOPLAY](../ia-et-multimedia/autoplay-qa-agent.md) et [FUTURE LEDGER](../outils-et-productivite/future-ledger.md). Aucun dépôt autonome ni expérimentation n'est créé par cette opération.
- Les passages antérieurs qui citent 14 idées décrivent des étapes historiques ; ils ne doivent pas écraser les index actuels.

## État historique — revue du 26 octobre 2026

Cette section documente le contenu actif tel qu'il était décrit à la date indiquée ; se référer à l'état actuel ci-dessus pour le catalogue en vigueur.

- **Quatorze idées retenues**, réparties entre `ia-et-multimedia/` (4), `infrastructure-et-medias/` (1), `communautes-et-echanges/` (1), `finance-et-crypto/` (3), `jeux/` (4) et `creatif-et-ecriture/` (1). La catégorie `education-et-pedagogie/` a été retirée après transfert de sa seule fiche.
- **Catégorie `creatif-et-ecriture/` réutilisée** pour l'idée de livre pédagogique sur l'investissement destinée à la famille, **exception éditoriale explicitement voulue** et non manuscrit déjà engagé.
- Les anciennes catégories `anime-et-media/`, `finance-et-recherche/` et `product-owner/` ont été retirées. **`jeux/` a été recréé uniquement pour cinq nouvelles idées de jeux explicitement demandées**, non pour les anciennes fiches supprimées. De même, le nouveau `finance-et-crypto/` ne rétablit PAS le dossier de discussions `finance-et-recherche/`. La fiche `server-monitor-dashboard.md` reste supprimée. **Ne pas recréer les anciennes fiches depuis les paragraphes historiques.**
- Les projets existants ont été comparés au périmètre des nouvelles idées : `chess-roguelite` ≠ échecs classiques à skins, `idle-clicker-tkinter` ≠ idle qui récompense l'absence, `bitcoin-wallet-education-lab` ≠ achat de BTC ou enseignement gamifié. **Ces distinctions ne constituent pas une garantie que les nouveaux projets ont été démarrés.** Revérifier les dépôts à chaque mise à jour.
- Règle de sortie : si l'utilisateur lance même une **recherche expérimentale versionnée**, créer le dépôt autonome d'abord, y transférer les documents puis supprimer l'idée de l'index. Les protocoles dans l'incubateur sont des plans, pas des travaux exécutés.
- Un thème de conversation, une œuvre déjà en travail ou une idée de logiciel que le propriétaire choisit de ne pas poursuivre ne constitue pas un projet à inscrire automatiquement.

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


## 2026-10-26 — Audit de cohérence demandé après nettoyage (résumé non verbatim)

**Utilisateur (verbatim ; heure exacte non attestée) :** « est-ce que toute la doc de l'incubateur est à jour ? Fait une passe rapide sur tous les fichiers de l'incubator et modifie/corrige ce qu'il faut »

**Assistant (résumé reconstruit, non verbatim) :** lecture du README racine, des index de catégories, de `AGENTS.md`, des deux documents de gouvernance/historique et des fiches restantes. Relecture des commits récents révélant la suppression ultérieure de `jeux/decklab.md` et `ia-et-multimedia/server-monitor-dashboard.md`, que les anciens index citaient encore. Suppression de l'index Jeux devenu vide, correction du README à **deux idées** et de l'index IA, renforcement des critères de sélection dans `AGENTS.md`, clarification du **moment de sortie de l'incubateur** dans les deux protocoles scientifiques. Cette opération est **documentaire seulement**, sans test scientifique ni création de projet.

**Erratum de l'état résiduel historique ci-dessus :** la note indiquant encore la présence de `finance-et-recherche/deep-tech-watch.md` reflétait un état **transitoire** ; ce fichier a ensuite été supprimé. Ne pas l'interpréter comme présent à la date de ce nouvel audit. Les catégories Finance, PO, Anime et Jeux sont maintenant absentes de la navigation ; la catégorie Créatif demeure volontairement vide.

**Vérification :** les fichiers et liens relatifs **connus des index** ont été contrôlés. Les références externes scientifiques sont des sources à revalider au démarrage d'un projet, pas une garantie de disponibilité ou de version pérenne. L'index Git doit rester la source de vérité.


## 2026-10-26 — Douze nouvelles propositions documentées dans l'incubateur

**Utilisateur (résumé fidèle, non verbatim ; heure exacte non attestée)** : demande de créer les catégories nécessaires et de documenter proprement douze idées listées « en vrac », en posant des questions seulement si nécessaire. Thèmes exacts identifiables : IA de génération cohérente de formations pour influenceurs ; IPTV personnel par curiosité ; entraide locale échangeant des services contre des points transférables au sein de la communauté ; recherche de marchés improbables sur Polymarket ; livre expliquant l'investissement à la famille sans donner de conseils ; romance à choix avec très nombreuses routes et ambiances à collectionner ; achat de Bitcoin par carte directement vers une adresse avec frais minimaux pour usage personnel ; échecs classiques et skins obtenus par gacha ; « Idle game - don't play » récompensant l'absence sans plafond de cumul ; « This ass does not exist » avec swipe ; jeu de plateforme speedrun découvrant progressivement des glitchs intentionnels ; application ludique expliquant les cryptomonnaies.

**Assistant (résumé non verbatim du travail effectué)** :
- 12 fiches dédiées, structurées en vision, cas d'usage, MVP, architecture hypothétique, recherche, contraintes et décisions à prendre : `ia-et-multimedia/generateur-formations-ia.md`, `infrastructure-et-medias/iptv-personnel.md`, `communautes-et-echanges/entraide-locale-points-temps.md`, `education-et-pedagogie/apprendre-crypto-en-jouant.md`, `finance-et-crypto/polymarket-marches-improbables.md`, `finance-et-crypto/bitcoin-carte-vers-adresse.md`, `creatif-et-ecriture/investissement-pour-ma-famille.md`, `jeux/romance-routes-collection.md`, `jeux/echecs-skins-gacha.md`, `jeux/idle-dont-play.md`, `jeux/this-ass-does-not-exist.md`, `jeux/speedrun-glitch-platformer.md`.
- Ajout des index des nouvelles catégories et mise à jour du catalogue principal : 14 idées = 2 préexistantes et 12 nouvelles. **Aucune application, livre ou prototype nouveau n'est déclaré démarré ni testé.**
- **Exception documentaire consciente** : le livre d'investissement reste une simple fiche de projet éditorial à lancer, parce que le propriétaire l'a demandé expressément, non un manuscrit public. Le contenu rédigé ira dans un espace de travail dédié lors du véritable démarrage.
- IPTV : usages licites uniquement ; Polymarket : interdiction d'ouverture de positions depuis la France au moment de la recherche (https://help.polymarket.com/en/articles/13364163-geographic-restrictions), donc analyse **lecture seule et simulation**, pas de contournement géographique ; BTC carte : flux uniquement par prestataire autorisé (régime PSCA/MiCA en France d'après https://www.amf-france.org/fr/espace-epargnants/proteger-son-epargne/crypto-actifs-bitcoin-etc/investir-en-crypto-monnaies-quel-professionnel-choisir).
- Les éventuelles catégories artificielles de genre ou de sexe dans un jeu d'images de corps fictifs ne sont **pas des inférences fiables d'identité** à partir de l'apparence. Fiche limitée à images synthétiques d'adultes non explicites et mécanique de catégorie fictive.
- Le propriétaire a **aussi** demandé huit besoins d'outillage Twitch (pastille santé plus sept modules). **Ne pas les inscrire ici** : projet déjà actif https://github.com/goldaj/twitch-streamer-dashboard. La vision complémentaire a été transférée à `docs/STREAMER_SUITE_BACKLOG.md` sur sa branche `develop`, et son contexte dans son `docs/CHATGPT_PROJECT_HISTORY.md`. Le voyant santé reste le premier MVP.

**À ne pas confondre :** un document détaillé et son cadrage ne constituent pas une recherche exécutée. Toutes ces fiches sont des hypothèses en attente de décision de démarrage et de transfert dans un dépôt autonome.


## 2026-10-26 — Reclassement ciblé de deux idées

**Utilisateur (verbatim, chemins conservés ; heure exacte non attestée)** :
> https://github.com/goldaj/projects-incubator/blob/main/jeux/this-ass-does-not-exist.md doit être déplacé dans https://github.com/goldaj/projects-incubator/tree/main/ia-et-multimedia
> https://github.com/goldaj/projects-incubator/blob/main/education-et-pedagogie/apprendre-crypto-en-jouant.md dans https://github.com/goldaj/projects-incubator/tree/main/finance-et-crypto

**Assistant (résumé non verbatim, opérations effectuées)** : fichiers déplacés avec **contenu strictement inchangé** de `jeux/this-ass-does-not-exist.md` vers `ia-et-multimedia/this-ass-does-not-exist.md`, et de `education-et-pedagogie/apprendre-crypto-en-jouant.md` vers `finance-et-crypto/apprendre-crypto-en-jouant.md`. Les anciens chemins ont été supprimés ; les README des catégories et l'index racine ont été rectifiés. Le dossier `education-et-pedagogie/` a disparu du HEAD Git, car devenu vide. **Total inchangé : 14 idées.**

Cette décision de classement **prime sur la liste historique des chemins d'origine** donnée plus haut, qui reste une trace des premières créations et ne doit pas être utilisée pour recréer les fichiers aux anciennes places.


## 2026-10-26 — Glitch Runner : cadrage de vitesse, inertie et anomalies (idée non démarrée)

**Utilisateur (verbatim ; date locale Europe/Paris, heure exacte non attestée) :**
> On va étoffer un peu [https://github.com/goldaj/projects-incubator/blob/main/jeux/speedrun-glitch-platformer.md](https://github.com/goldaj/projects-incubator/blob/main/jeux/speedrun-glitch-platformer.md)
> Pour l'instant on laisse ça dans l'incubator et on ne code pas. Mais ça sera peut être un des projets sujets auquel on s'attaque.
>
> Réfléchis, recherche, détermine la faisabilité. On part de quelque chose de simple mais subtile, comme la complexité d'un SMB3 par exemple, mais sans le copier, juste dans la simplicité je veux dire. Et surtout on veut une satisfaction de vitesse et d'inertie à la sonic, dans anciens jeux 2D.
> En gros il faut vraiment la fierté de passer les glitchs et la satisfaction du résultat de vitesse qui était coupé dans son élan/impossible à avoir si on avait joué normalement.

**Assistant (résumé reconstruit, non verbatim) :**
- Lecture des fichiers existants `jeux/speedrun-glitch-platformer.md`, `README.md`, `AGENTS.md`, des conventions de passation et de ce journal.
- Recherche documentaire sur la physique 2D des premiers Sonic, les techniques de mouvement dans Celeste, le design de vitesse de Pizza Tower et la simulation à pas fixe de Godot. Sources et limites citées dans la fiche.
- Positionnement recommandé : jeu 2D simple et lisible, mouvement plaisant sans glitch, **glitch exécuté avec les commandes ordinaires**, et surtout conservation de l'élan permettant **une prouesse de vitesse / hauteur normalement interdite**.
- Proposition de deux techniques **hypothétiques** combinables : `Corner Slip` (franchissement maîtrisé d'une jonction de collision) et `Slope Overflow` (projection exceptionnelle à partir d'une rupture de pente), sans les présenter comme déjà validées.
- Ajout d'un modèle conceptuel du mouvement, des exigences de caméra, du jeu à trois niveaux de maîtrise, d'un MVP ramené à quatre espaces, de risques, protocoles de validation H1–H5 et plan de reprise futur P0–P6.
- Distinction expresse entre **faisabilité technique plausible** et **plaisir de jeu non prouvé** ; avertissement sur l'absence de déterminisme multiplateforme automatique et sur la difficulté principale (réglage du mouvement + niveau).
- **Aucun code, aucun essai réel, aucun dépôt séparé créés.** Mise à jour documentaire uniquement sur `main`. Le projet demeure une fiche à démarrer. Quand il démarrera, transférer le cadrage dans le dépôt dédié et enlever la fiche de l'index.
- Le texte de ce résumé n'est pas une transcription littérale du message complet de l'assistant ; l'historique préexistant demeure partiel.

## 2026-10-27 — Glitch Runner quitte l'incubateur pour un dépôt autonome

**Utilisateur (verbatim, heure exacte non attestée) :**
> j'ai créé ce repo : [https://github.com/goldaj/glitch_runner](https://github.com/goldaj/glitch_runner)
> On va commencer à bosser sérieusement dessus.
> On prends les mêmes consignes que toutes les conversations qu'on a eu ensemble du type "Avancement_projets_codex_8"
>
> Et en avance !

**Assistant (résumé reconstruit, non verbatim) :** dépôt confirmé ; création de branche de développement `feat/foundation-movement-p1`, copie intégrale du concept vers [docs/INCUBATOR_CONCEPT.md](https://github.com/goldaj/glitch_runner/blob/feat/foundation-movement-p1/docs/INCUBATOR_CONCEPT.md), plan scientifique, AGENTS, historique, laboratoire Godot P1 avec tests et CI. Aucune validation du game feel revendiquée. Retrait de la fiche d'idée et de sa navigation sur branche distincte `chore/graduate-glitch-runner`, destinée à PR **sans fusion automatique**. Les anciennes sections de ce fichier décrivent l'incubation historique, non l'état présent.

**Source de vérité après migration :** https://github.com/goldaj/glitch_runner ; l'ancien concept demeure dans l'historique Git et dans la copie figée du nouveau dépôt.

## 2026-10-31 — Sélection puis inscription de trois nouveaux projets

**Source :** conversation visible « Avancement pour Codex », messages disponibles dans cette session. Texte cité uniquement quand il est accessible ; heure précise non attestée.

**Utilisateur (verbatim) :**
> Avec tout ce que tu sais de moi et de mes projets déjà en cours sur GitHub, propose moi 3 nouveaux sujets ; 1 de recherche, 1 d'IA, 1 de développement de logiciel

**Assistant (résumé reconstruit, non verbatim) :** propositions initiales RETRO-LAB, AUTOPLAY et Romance Radar ; rapprochement des dépôts actifs et des idées déjà enregistrées.

**Utilisateur (verbatim) :**
> Non romance radar c'est nul. Fait 3 autres propositions pour remplacer ce sujet là

**Assistant (résumé reconstruit, non verbatim) :** trois alternatives logicielles : REPLAY, PAGE ZERO et FUTURE LEDGER.

**Utilisateur (verbatim) :**
> On part sur le 3.
> Garde du coup les 2 premières idées, puis là la 3e proposition pour la 3e idée.
> Recupitule moi ça

**Assistant (résumé reconstruit, non verbatim) :** confirmation du trio RETRO-LAB (recherche), AUTOPLAY (IA) et FUTURE LEDGER (logiciel). Romance Radar est rejeté ; REPLAY et PAGE ZERO ne sont pas sélectionnés ici.

**Utilisateur (verbatim) :**
> Good. Enregistre ces 3 idées dans GitHub sur l'incubator et développe un peu les sujets

**Assistant (résumé du travail réalisé) :** trois fiches autonomes avec vision, premières fonctionnalités, méthode d'évaluation, MVP, limites, distinction des dépôts existants et questions ouvertes. Mise à jour des index et des décomptes. Travail **documentaire uniquement** dans l'incubateur ; les dépôts suggérés ne sont pas créés.

**Reprise Codex :** pour chaque idée choisie au démarrage, créer un dépôt dédié et y transférer la fiche avant de démarrer une recherche versionnée ou le développement ; retirer alors la fiche des index de l'incubateur. Ne pas confondre hypothèse et validation obtenue.
