# Buy Bitcoin and Fuck Off — achat BTC vers une adresse, sans friction

**Statut : idée d'outil personnel non démarré, non commercial.** Nom de travail volontairement provocateur, à ne pas confondre avec un service financier opérationnel.

## Promesse UX
Une interface aussi simple que possible :
1. Saisir ou scanner **une adresse Bitcoin de réception**.
2. Choisir le montant en euros.
3. Voir **avant confirmation** : quantité BTC estimée, coût par carte, spread, frais réseau, montant BTC net attendu, limites et délai.
4. Payer auprès d'un prestataire externe habilité.
5. Suivre l'opération et obtenir le TXID ou un état d'exécution traçable.

**Principe non négociable :** pas de conservation de fonds, ni de gestion de clés privées par notre application, ni de portefeuille inventé, ni d'échange opéré par nous. Le paiement, les vérifications KYC/AML et le transfert doivent être effectués **par un acteur autorisé** ; l'application n'est qu'une interface ou redirection, sous réserve de qualification juridique.

## Réalité économique à étudier
Le « minimum de frais » ne peut pas être garanti : carte bancaire, conversion, spread, réseau Bitcoin, coût du prestataire et minimum d'achat. Comparer coûts **effectifs tout compris** pour plusieurs montants, débits de carte, délais, réputation et capacité d'envoi vers une adresse externe. Mesurer combien d'étapes obligatoires restent même dans le meilleur flux.

## MVP conceptuel sans transaction
Interface statique interactive avec validation checksum de l'adresse et réseau, choix de montant, comparaison **indicative** de 2 ou 3 parcours de prestataires autorisés (données de prix réelles ultérieurement), confirmation détaillée puis redirection officielle vers l'interface d'achat du prestataire. **Aucun paiement direct ni échange intégré dans un premier pilote.**

## Architecture et sûreté
UI/PWA légère, éventuel mini backend proxy pour devis, aucun identifiant secret dans le client ; stockage minimal ou nul. Verrouiller destination après confirmation, afficher le réseau et valider les adresses (Legacy, SegWit, Taproot), empêcher l'adresse modifiée par presse-papiers malveillant et les confusions on-chain/Lightning. Ne jamais inférer propriété de l'adresse ; relecture visuelle et avertissement transaction irréversible.

## Cadre réglementaire
L'AMF précise qu'en France, depuis le **1er juillet 2026**, les prestataires fournissant des services sur crypto-actifs doivent disposer du statut **PSCA** sous MiCA. Une application personnelle sans fonds de tiers réduit le périmètre, mais la **réception/transmission d'ordres, la fourniture de services de transfert et la distribution d'achats** peuvent relever de services réglementés selon l'intégration exacte. Vérification juridique et de l'accord du prestataire **avant** connexion de paiements réels. Source : https://www.amf-france.org/fr/espace-epargnants/proteger-son-epargne/crypto-actifs-bitcoin-etc/investir-en-crypto-monnaies-quel-professionnel-choisir .

## Hypothèses et tests
Comparer trois flux : lien officiel prérempli, widget partenaire autorisé, simple assistant de comparaison. Métriques : clics, prix réel net en BTC, clarté du devis, sécurité de l'adresse, friction légale. L'outil n'a aucun lien avec `bitcoin-wallet-education-lab`, qui conserve des prototypes pédagogiques non validés de cryptographie.

## Questions ouvertes
Bitcoin on-chain uniquement ou Lightning également ? Carte uniquement ou SEPA en option pour économiser les frais ? Prestataires disponibles en France et règles d'intégration ? Contrôle de frais maximal ou prix final minimal ?
