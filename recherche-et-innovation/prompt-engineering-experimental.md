# Prompt Engineering Lab — recherche expérimentale sur les instructions aux IA

**Statut : idée incubée, sans développement ni expérimentation exécutée.** Fiche de cadrage et première analyse documentaire, au 31 octobre 2026. Aucune performance propre revendiquée.

**Origine :** idée N-0003 du registre privé Notepad. Transfert explicitement demandé le 31 octobre 2026. La note d'origine et son verbatim restent privés dans Notepad ; le registre y porte le statut « transférée », pas « supprimée ».

## Objectif et modèles cibles

**Priorité P1 — OpenAI actuels :** GPT-6 Astra (gpt-6-astra), GPT-6.1 Sol (gpt-6.1-sol), GPT-6.1 Terra (gpt-6.1-terra), chacun dans les interfaces et niveaux d'effort effectivement disponibles.

**Priorité P2 — transférabilité générale :** découvrir les effets robustes entre tâches, familles de modèles et conditions d'inférence ; inclure par la suite d'autres fournisseurs et modèles ouverts comme témoins pour éviter de suradapter la recherche à OpenAI.

**Priorité P3 — Jade :** réappliquer les méthodes à Jade lorsqu'elle disposera de son moteur d'inférence propre. Prévoir dès maintenant un adaptateur local compatible avec les métriques, les jeux de tests et le stockage des traces, sans supposer son architecture finale, sa taille ni ses capacités.

**Objectif scientifique :** identifier quelles formulations, quels modes d'organisation des tâches et quels dispositifs de vérification améliorent **effectivement** la qualité, la fiabilité et le coût total d'une réponse pour une combinaison tâche-modèle donnée. Chercher des règles conditionnelles, non un « prompt universel ».

**Objectif pratique :** améliorer progressivement la collaboration humaine/IA sur recherche, code, revue, documentation, décisions et tâches longues, en particulier les sessions ChatGPT/Codex, puis les capacités futures de Jade.

## Ce que l'on compare (variables indépendantes)

- **Cadrage des instructions :** demande brève directe, consignes complètes, critères d'acceptation, exemples / contre-exemples, rôle/persona, consignes négatives ou positives.
- **Raisonnement :** réponse directe, demande de justification vérifiable, décomposition en sous-tâches, demande « réfléchis étape par étape » ; séparer la formulation du paramètre de *reasoning effort* et ne pas demander de dévoiler des raisonnements internes cachés.
- **Déroulement :** un seul appel, plan puis exécution, exécution puis contrôle, itération critique, agents/outils, auto-évaluation et évaluation indépendante.
- **Contexte :** quantité et position des documents, contexte utile/bruit, exemples pertinents ou non, format des instructions et hiérarchie des consignes, mémorisation / récupération.
- **Sortie :** langage naturel vs schéma structuré, niveau de verbosité demandé vs paramètre de verbosité disponible, checkpoints et preuves.
- **Optimisation :** sélection de prompts manuelle vs APE/OPRO, compilation DSPy, évolution réflexive GEPA ; contrainte de budget et validation hors-échantillon.
- **Interaction tâche × modèle :** mêmes familles de tâches, mêmes critères, plusieurs répétitions et analyses séparées pour Astra, Sol et Terra.

## Différencier les environnements

1. **API OpenAI :** cible principale pour des expériences automatisées, si l'accès API existe et si un budget de tests est approuvé. Les abonnements ChatGPT/Codex ne doivent pas être considérés comme des crédits API interchangeables. Utiliser les identifiants de modèles réellement accessibles, fixer les paramètres applicables et conserver les réponses et métadonnées autorisées.
2. **ChatGPT et Codex :** études écologiques sur de vrais workflows, avec instrumentation plus limitée. Documenter les réglages visibles, les contraintes de contexte, les outils, la configuration et l'absence de contrôles expérimentaux impossibles. Ne pas automatiser une interface ou un quota qui ne l'autorise pas.
3. **Jade locale :** futur adaptateur générique de génération ; mesurer tokens, latence, RAM/VRAM et conditions matérielles, quantification, longueur de contexte et seed seulement si supportée. Comparer **à modèle et ressources constants**, puis étudier explicitement les écarts entre modèles.

## Critères de réussite et falsifiabilité

- **Primaire :** taux de réussite sur des tâches à oracle externe / tests exécutables / réponses vérifiables, par famille de tâche.
- **Secondaires :** respect des instructions, erreurs factuelles sourcées, qualité du code confirmé par tests, temps humain de reprise, robustesse sur variantes, coût monétaire et token, latence p50/p95, validité des formats.
- **Biais à contrôler :** préférence du juge LLM pour son propre style, position des réponses, fuite de données, prompts trop longs, benchmark contaminé, variance entre essais, dérive des snapshots de modèle, confusions de paramétrage.
- **Comparaisons :** mêmes inputs, tests appariés, sous-ensembles de développement/validation/test distincts, randomisation de l'ordre, préenregistrement des métriques et analyse des incertitudes.
- **Échec instructif :** si l'amélioration est nulle, instable, trop chère ou ne se transfère pas, documenter ce résultat et ne pas promouvoir la recette.

## Première campagne proposée, NON exécutée

**Pilote méthodologique (phase de démarrage après création d'un dépôt dédié) :**
- 36 tâches anonymisées avec oracle : 12 extraction structurée et contradictions documentaires, 12 développement/correction de code avec tests isolés, 12 recherche/réponse sourcée et contrôle humain + règles.
- Pour chaque modèle accessible, comparer 4 variantes : (A) demande courte, (B) objectifs/contraintes/acceptance tests explicites, (C) B + exemples pertinents, (D) B + décomposition/contrôle externe. Répéter 2 fois, équilibrer l'ordre.
- 36 × 4 × 2 = **288 requêtes par modèle** ; 864 si les 3 modèles sont tous disponibles et financés, sans compter les essais d'outils ou optimisateurs. **Ceci est un dimensionnement, pas une expérience lancée ni un budget approuvé.**
- Comparer les conditions à effort de raisonnement identique lorsque possible ; un deuxième bloc séparé fera varier l'effort, le mode d'outillage et le coût pour les tâches difficiles.
- Réserver à part un petit ensemble test jamais présenté à l'optimiseur ; retirer les tâches dont l'oracle dépend de faits volatils non datés.
- Publier résultats détaillés, intervalles de confiance, cas d'échec et coûts estimés après mesures, sans inventer de gains.

**Plan d'étude préliminaire immédiat :** lire et critiquer les sources, définir les familles de tâches et les critères, vérifier les accès API / outils / coûts, lister les risques de contamination et construire un préenregistrement. Aucun appel aux modèles et aucune expérience comparative n'ont été effectués par cette fiche.

## Décisions d'architecture pour le futur dépôt expérimental

- Interfaces adaptatrices pour fournisseurs/modèles, version du modèle et paramètres.
- Jeux de tâches versionnés, manifestes de prompts, réponses et résultats append-only, checksums ; provenance et coûts.
- Exécution sandboxée des tests logiciels ; aucun code non fiable sur le système hôte.
- Juges de référence indépendants des prompts optimisés ; double évaluation en aveugle pour tâches subjectives.
- Tableaux de bord séparant **moyenne, distribution et coût**, sans choisir a posteriori uniquement la meilleure configuration.
- Adaptateur Jade défini par contrat de génération, non par hypothèse sur son futur moteur.

## Documentation de l'état de l'art

Voir [État de l'art initial et protocole critique](etat-art-prompt-engineering-2026-10-31.md). L'étude distingue résultats publiés, conseils de fournisseur et **hypothèses personnelles à tester**.

## Frontières et cycle de vie

Il s'agit d'un programme de recherche **non démarré**, au sens de l'incubateur. Une analyse documentaire et un protocole proposé dans cette fiche n'impliquent ni résultats expérimentaux ni développement actif. Au lancement effectif de la recherche versionnée, créer un dépôt autonome et y transférer ce dossier ; retirer alors la fiche de cet index, tout en préservant son historique Git.

**Aucune donnée personnelle, secret, historique privé de conversation ni document de dépôts privés ne doit être transféré vers cet incubateur public.**
