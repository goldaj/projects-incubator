# AGENTS.md — Projects Incubator

## Avant de travailler
1. Lire `README.md` et les documents techniques pertinents, puis **`docs/CHATGPT_PROJECT_HISTORY.md`** pour les demandes, décisions et lacunes du contexte.
2. Index public strictement réservé aux idées NON DÉMARRÉES **et que le propriétaire souhaite réellement conserver comme futurs projets**. Les discussions non destinées à un logiciel, veilles, œuvres déjà engagées et suggestions retirées n'y ont pas leur place. Les projets commencés, y compris avec un simple protocole ou prototype versionné, sont retirés de l'incubateur.
3. Avant tout ajout, vérifier qu'aucun dépôt Git dédié (même sous un autre nom) n'exécute déjà l'idée. Après démarrage, supprimer la fiche et le lien de navigation ; ne conserver un concept voisin que si son autonomie a été explicitement établie, et non en inventant une différence de périmètre. Ne pas publier de secrets, manuscrits, données privées ou configuration personnelle.

## Exécution et vérification
- Valider **tous les liens relatifs des index**, le nombre de fiches réellement présentes, le classement et les dossiers vides à chaque modification ; aucune commande de build générale.
- Si une catégorie doit rester volontairement vide, conserver son `README.md` (Git ne versionne pas de dossier vide). Les autres catégories sans fiche active sont à retirer de la navigation et du dépôt.
- Utiliser de petites modifications contrôlables. Ne pas écraser ni supprimer des fichiers ou anciennes versions sans demande explicite.
- Distinguer hypothèses, code présent, essais effectivement exécutés et éléments encore à valider.

## Passation à Codex et archivage permanent
- **Document de référence de la conversation :** `docs/CHATGPT_PROJECT_HISTORY.md` ; il peut être incomplet et le dit explicitement.
- Après chaque intervention, mettre à jour ce document si une décision, une contrainte, une étape ou un nouveau contexte pertinent change. Référencer les nouveaux messages de l'utilisateur et de l'assistant lorsque leur texte exact est accessible.
- Format : date ISO et fuseau si connus, rôle `Utilisateur` ou `Assistant`, mention `verbatim` seulement pour un texte exact. Sinon `résumé reconstruit, non verbatim`. Ne pas inventer d'heure ni de citation.
- Si l'historique intégral n'est pas disponible, le signaler et demander un export réel plutôt que fabriquer une transcription. Préserver les exports existants sans les réécrire.
- Exclure secrets, identifiants, données personnelles et contenus non destinés à la publication. Le niveau de visibilité de ce dépôt s'applique aussi aux documents ajoutés.


## Convention commune aux dépôts

Appliquer aussi [la convention de continuité ChatGPT/Codex](docs/GITHUB_CODEX_CONTEXT_POLICY.md) pour chaque nouveau dépôt ou modification : AGENTS.md, journal de contexte sourcé et mise à jour des échanges disponibles, sans inventer de transcription.
