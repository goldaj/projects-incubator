# Coup de main — réseau local d'entraide à points de temps

**Statut : idée à démarrer.** Plateforme web/mobile pour voisins ou membres d'une même communauté. **Origine :** demande du 26 octobre 2026.

## Concept, invariant central
Un membre rend un service à quelqu'un et reçoit des **crédits communs**, qu'il peut dépenser auprès de **n'importe quel autre membre**. Ce n'est **pas du troc bilatéral**. Règle initiale proposée : **1 heure de service reconnu = 1 crédit**, indépendamment du métier, sous réserve de l'accord de la communauté et d'une granularité à définir.

> Exemple : Alice aide Bob à jardiner pendant une heure. Alice reçoit 1 point ; elle l'utilise la semaine suivante pour une heure de cuisine proposée par Chloé. Bob ne doit rien à Alice directement.

## Parcours de référence
1. Inscription, vérification légère de la communauté ou quartier, pseudonyme/publication de profil limitée.
2. Publication d'une **demande** ou d'une **offre** : activité, durée envisagée, lieu approximatif, disponibilité, matériel, limites.
3. Mise en relation par recherche et compatibilité horaires / proximité.
4. Accord sur durée et conditions, confirmation du service par les deux parties.
5. Débit/crédit atomique dans un **registre traçable**, consultation du solde et historique, contestation possible.
6. Points dépensables auprès de tout membre ; garde-fous contre comptes factices et fraude circulaire.

## Problèmes à étudier d'abord
- **Amorçage économique** : qui aide au début quand personne n'a de crédits ? Crédit de bienvenue plafonné, dette contrôlée, points non transférables, cagnotte commune ? Simuler séparément les politiques.
- **Liquidité locale** : certaines offres sont très demandées, d'autres peu ; mesurer délai de mise en relation, taux de demandes satisfaites, distribution des soldes et membres inactifs.
- **Équité** : 1 point/heure favorise simplicité et réciprocité, mais ne tient pas compte du matériel, des compétences ou du risque ; prévoir frais matériels hors points et catégories réglementées exclues.
- **Confiance** : identité minimale, signalement, annulations, fraude, comportements abusifs, rencontre chez des inconnus, sécurité, mineurs, responsabilité et assurance.
- **Cadre légal** : qualification du service rendu, obligations fiscales/sociales éventuelles, RGPD, travail dissimulé ou activité professionnelle déguisée selon fonctionnement réel. **Ne pas annoncer une exemption juridique parce qu'aucun euro ne circule.**

## MVP volontairement étroit
Une seule communauté pilote, 20 à 50 membres volontaires adultes ; offres/demandes ; recherche ; réservation ; confirmation mutuelle ; points entiers ou demi-heures ; historique append-only ; modération manuelle ; pas de portefeuille crypto, paiement, IA, géolocalisation précise ni réputation publique irréversible.

## Modèle technique suggéré
Web responsive/PWA ; PostgreSQL transactions sérialisables ou ledger double entrée (écriture de crédit/débit liée à un `service_id`) ; règles de solde et anti-double-validation ; identités communautaires ; notifications optionnelles ; journal d'audit et mécanismes d'annulation compensatoire ; sauvegardes/restauration.

## Test et métriques
D'abord simuler 100 échanges avec 3 politiques d'émission de crédits ; ensuite pilote de quartier. Suivre échanges réellement accomplis, demandes satisfaites, crédits inutilisables, concentration, abus et coût de modération. **Succès = services échangés et confiance, pas simple nombre de comptes.**

## Questions de produit
Communauté ouverte par voisinage ou uniquement sur invitation ? Exiger réciprocité en temps strict ? Peut-on avoir un solde négatif ? Comment payer les matières premières ? Les décisions appartiendront au propriétaire après recherche.
