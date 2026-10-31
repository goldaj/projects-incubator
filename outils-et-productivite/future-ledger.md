# FUTURE LEDGER — Journal de prédictions et calibration personnelle

**Statut : idée d'application non démarrée.** Retenue explicitement le 31 octobre 2026 pour remplacer la proposition « Romance Radar », explicitement rejetée. Aucun outil, compte utilisateur ni scoring réalisé. **Dépôt autonome envisagé :** future-ledger.

## Proposition
Enregistrer des prédictions **horodatées, précises et probabilisées**, puis mesurer, une fois les événements résolus, à quel point nos jugements étaient correctement calibrés.

L'application doit rendre difficiles les réinterprétations a posteriori : conserver l'énoncé d'origine, la probabilité, les motifs, les modifications et les règles de résolution. L'objectif est d'améliorer le raisonnement, pas de simuler une boule de cristal.

## Parcours utilisateur cible
1. Formuler une question binaire résoluble : « L'événement X sera-t-il observé avant le 31 décembre 2032 ? ».
2. Définir **avant de prédire** ce que signifie OUI/NON, l'échéance, la source de référence et le cas où les données restent indisponibles.
3. Enregistrer sa probabilité de 0 à 100 %, ses arguments, éléments de preuve et éventuelles hypothèses.
4. Réviser la probabilité dans le temps sans effacer les versions passées. Chaque version garde sa date ; un résultat connu ne peut pas être injecté rétrospectivement.
5. À la résolution, ajouter résultat (oui/non/non résoluble), source et justification. Prévoir une correction auditée en cas d'erreur de résolution.
6. Afficher score, taux de résolution, calibration et biais éventuels **sur un ensemble suffisant** de prédictions.

## Moteur de mesure
Pour une prédiction binaire de probabilité p dans [0,1] et un résultat o (0 ou 1), le **score de Brier = (p - o)²** : 0 est idéal, 1 le pire. Afficher la moyenne des scores et des courbes de calibration par tranches de probabilité, avec tailles d'échantillons. Un score individuel n'établit pas une capacité prédictive, et une bonne calibration n'est pas synonyme de précision ou de pouvoir explicatif.

Séparer les prévisions initiales des révisions, et annoncer explicitement la règle de scoring retenue (par exemple première prévision, dernière prévision avant clôture, ou score temporel). Ne jamais optimiser opportunément la règle après connaissance des résultats.

## MVP concret
- Web responsive, usage personnel sans compte dans une première version locale.
- Création, recherche, catégories et échéances de prédictions binaires.
- Versionnement non destructif des probabilités et arguments ; export JSON/CSV.
- Résolution manuelle avec source vérifiable et motif.
- Dashboard : résultats résolus/non résolus, score de Brier moyen, répartition des probabilités, graphique de calibration et avertissement sur faible échantillon.
- Jeu de données fictif et tests automatisés pour les calculs, dates et impossibilité de modifier silencieusement l'historique.

Premier objectif d'usage : enregistrer 20 prédictions dans plusieurs domaines et vérifier que toutes pourront être résolues sans changer la question après coup. **Aucun score réel n'est revendiqué à ce stade.**

## Extensions possibles, à ne pas confondre avec le MVP
- Comparaisons entre participants, classement sous règles homogènes et opt-in.
- Prédictions numériques ou intervalles avec scores adaptés, clairement séparés du Brier binaire.
- Suggestions de taux de base et rappel des résolutions, sans recommandation d'investissement.
- Indicateurs personnels de surconfiance, pessimisme, sous-pondération des faits nouveaux.
- Rapprochement avec des sources officielles pour proposer une résolution, **jamais sans source et piste d'audit**.
- Journal de décisions : comparer une décision prise et la qualité de la prédiction qui l'a motivée, sans confondre qualité de décision et chance.

## Architecture candidate
Frontend web + base locale SQLite ou IndexedDB (à arbitrer) + moteur de scoring pur et testé + schéma versionné (Question, Rules, ForecastRevision, Evidence, Resolution, AuditEvent). Synchronisation et comptes multi-utilisateurs seulement si besoin avéré. Export portable et confidentialité par défaut.

## Frontières et risques
Ce projet n'est **ni une application de paris**, ni un scanner de marchés prédictifs, ni un bot de trading. Ne jamais proposer de mises, achat de contrats, transactions ou stratégies financières à partir des scores. La principale difficulté est la **qualité des questions et des résolutions** : ambiguïté, sélection de prévisions faciles, événements dépendants, retard des sources, biais de survivance, petit échantillon et fuite d'information après l'échéance.

## Questions ouvertes
Faut-il autoriser les prévisions privées uniquement ou une publication volontaire ? Comment gérer les questions non résolubles ? Quel protocole comparer pour les révisions ? Quelles règles prévenir contre les classements manipulables ?

**Passage à l'action :** créer le dépôt autonome et y transférer ce cadrage avant toute implémentation, puis retirer la fiche de l'incubateur.
