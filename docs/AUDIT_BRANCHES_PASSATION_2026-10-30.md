# Audit des branches et passation de l'incubateur — 30 octobre 2026

## Périmètre
Ce dépôt **public** recense uniquement les projets futurs non démarrés que le propriétaire veut conserver. Les projets disposant déjà d'un dépôt dédié doivent être retirés de l'incubateur ; une fiche historique maintenue comme projet actif serait trompeuse. Éviter toute publication de manuscrit, données privées ou secrets.

## Branches (base `main`)
- `main` : `2d77cf6e801ca4a33167d925974df686316c5fe4`.
- `chatgpt/research-prioritization-20261025` : `75b058401193f7d7fbc892c3a3ce753b97b427d1` ; behind, ahead 0, behind 10. Historique intégré, candidate au nettoyage après vérification des références.
- `chore/archive-japan-ar-idea` : `8ac49766bfed7a03a647c070370a78d8e18e528c` ; behind, ahead 0, behind 107. Historique intégré, candidate au nettoyage après vérification des références.
- `chore/archive-twitch-stream-dashboard` : `45d4b6662df5f594fc98d705409d923bdfecf9c5` ; behind, ahead 0, behind 104. Historique intégré, candidate au nettoyage après vérification des références.
- `chore/archive-vtube-physics-and-live2d-lab` : `f4847dacc7285fa85ce7c1061eeaf80a4b29049d` ; behind, ahead 0, behind 80. Historique intégré, candidate au nettoyage après vérification des références.
- `chore/graduate-glitch-runner` : `7ef979909fd8e72ad3e0acc8ccb0ff9006ccbc93` ; behind, ahead 0, behind 23. Historique intégré, candidate au nettoyage après vérification des références.

## PR (5)
- [#5](https://github.com/goldaj/projects-incubator/pull/5) : fusionnée ; `chore/graduate-glitch-runner` → `main`.
- [#4](https://github.com/goldaj/projects-incubator/pull/4) : fusionnée ; `chore/archive-vtube-physics-and-live2d-lab` → `main`.
- [#3](https://github.com/goldaj/projects-incubator/pull/3) : fusionnée ; `chore/archive-twitch-stream-dashboard` → `main`.
- [#2](https://github.com/goldaj/projects-incubator/pull/2) : fermée sans fusion ; `chore/archive-japan-ar-idea` → `main`.
- [#1](https://github.com/goldaj/projects-incubator/pull/1) : fusionnée ; `chatgpt/research-prioritization-20261025` → `main`.

## Challenger la gouvernance et les liens
- Vérifier tous les index et liens relatifs ; une catégorie vide ne peut être représentée que par un README de conservation volontaire. Contrôler la cohérence des comptes de fiches avec les véritables fichiers, sans déduire du seul README.
- Les travaux Japan AR, VTube Physics, Glitch Runner et Twitch Stream Dashboard possèdent des dépôts et doivent être qualifiés de projets lancés, pas d'idées actives ici.
- Revoir le classement des fiches déplacées, notamment `this-ass-does-not-exist` dans IA/multimédia et la pédagogie crypto dans Finance/crypto, sans réintroduire de duplicats ni déplacer des pistes sans instruction.
- Les notes de Notepad et décisions mensuelles ne sont pas automatiquement des idées autonomes à publier ; protéger les sources privées.

## Reprise prioritaire
Lire `README.md` (« # Project Incubator | Idées à démarrer »), `AGENTS.md`, `docs/CHATGPT_PROJECT_HISTORY.md`. Exécuter un validateur de liens locaux/index/fiches, comparer les noms de dépôts dédiés et signaler chaque orphelin/ambiguïté, puis produire un rapport **sans modification de fonds**. Aucun test ou contrôle automatisé exécuté pendant cet audit ; seul ce document est ajouté. Pas de branches supprimées.
