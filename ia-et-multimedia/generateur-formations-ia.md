# AI Course Factory — Générateur de formations cohérentes pour créateurs

**Statut : idée à démarrer.** Projet logiciel nouveau, aucun produit ni modèle entraîné ici. **Origine :** demande du propriétaire du 26 octobre 2026.

## Vision et proposition de valeur
Permettre à un influenceur, créateur de contenu ou expert qui vend des formations de produire en une session **un cours structuré, pédagogique et publiable d'une qualité respectable**, plutôt qu'un assemblage de diapositives IA contradictoires. La promesse à éprouver est le **gain de temps avec cohérence mesurable**, pas « zéro erreur » garanti.

## Parcours utilisateur cible
1. Répondre à un entretien guidé court : sujet précis, promesse pédagogique, public, prérequis, ton, longueur, expertise, exemples autorisés, sources de référence.
2. Déposer des notes, contenus personnels, liens ou documents pour fixer la source de vérité ; identifier explicitement ce qui est opinion, expérience ou fait vérifié.
3. L'IA propose **objectifs observables**, plan global, modules, chapitres, exemples et exercices. L'utilisateur valide ou édite ce contrat de cours une seule fois.
4. Générer progressivement scripts, supports, fiches, quiz, corrigés, résumé et éventuellement narration ; exporter en formats simples.
5. Exécuter un **audit transversal** : contradictions entre sections, prérequis manquants, définitions changeantes, affirmation non étayée, quiz hors programme, promesse marketing non tenue.
6. Corriger de façon localisée, montrer les points incertains et offrir une validation humaine finale avant toute diffusion.

## Différenciation et questions de recherche
- Une **base de faits partagée** (terminologie, thèses, exemples, conventions, exclusions) et un graphe de dépendances pédagogiques évitent qu'un chapitre 8 contredise le chapitre 2.
- Pipeline multi-étapes plutôt que génération monolithique : `brief → syllabus approuvé → matrice d'objectifs → contenu → contrôles → révisions → export`.
- Évaluer les méthodes : vérification par règles, citations alignées aux sources, second modèle contradicteur, comparaison des engagements du syllabus, tests de quiz et contrôle humain.
- Mesurer hallucinations, incohérences internes, couverture des objectifs, répétitions, durée de production, coût en tokens et proportion des corrections acceptées.
- Déterminer si une production intégralement « one shot » est réaliste ou si **une validation initiale de deux minutes** améliore davantage la qualité.

## MVP testable
Formulaire de brief, import Markdown/PDF/licites, plan validable, génération de 3 modules et exercices, audit de cohérence avec liens vers passages concernés, export Markdown + PDF/HTML. **Pas de vidéo avatar, LMS complet, montage automatique ni publication commerciale en V1.**

## Architecture candidate, à challenger
Frontend web ; orchestrateur de jobs idempotents ; base de connaissances de projet versionnée ; schéma structuré `Course → Objective → Module → Lesson → Claim → Source → Exercise` ; LLM(s) API interchangeable(s) ; exports asynchrones. Garder révisions, coûts, provenance des affirmations et progression. Réduire contexte répété par références croisées structurées.

## Risques et limites
Fausse expertise, promesse de réussite infondée, erreurs dans les domaines sensibles, droit d'auteur sur supports importés, confidentialité des documents, formation trompeuse ou copiée, droits sur voix/identité. L'outil doit **signaler ses incertitudes**, pas certifier la vérité ni permettre de vendre sciemment de fausses qualifications.

## Ordre de recherche avant code
R0 : état de l'art des générateurs et LMS, test sur 3 domaines différents. R1 : définir 20 incohérences typiques et un corpus annoté. R2 : comparer pipeline one shot vs étapes validées. R3 : mesurer rapport temps/qualité/coût. Puis décider d'un repo dédié et supprimer la fiche ici.

## Questions ouvertes
Quels exports prioritaires (PDF, diapos, SCORM, vidéo) ? Cible débutant ou créateur déjà équipé d'un LMS ? Validation de sources externes obligatoire ? Édition de marque blanche ? **Hypothèses, pas décisions prises.**
