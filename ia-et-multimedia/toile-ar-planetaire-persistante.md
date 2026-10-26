# Toile AR planétaire persistante — le monde entier comme tableau partagé

**Statut : IDÉE À DÉMARRER / recherche préalable, aucun prototype engagé.**  
**Date du cadrage : 2026-10-26.**  
**Catégorie : réalité augmentée / géospatial / systèmes distribués / interaction humain-environnement.**  
**Nom de travail : World Canvas / Toile AR planétaire (provisoire).**

> **Vision :** un utilisateur regarde le monde réel avec son téléphone ou des lunettes de réalité augmentée, trace une ligne ou écrit dans l'espace. Cette inscription demeure **attachée à un endroit physique précis, y compris en hauteur**, et devient visible à **toute autre personne utilisant l'application**, même plus tard. À terme, la planète entière sert de toile, sans précharger la planète sur les appareils.

Ce document est une **fiche d'incubation scientifique et technique**, pas la preuve d'un système existant ni une autorisation de commencer à coder. Une seule petite zone sera étudiée d'abord. Aucune décision fournisseur ni précision garantie ne sont actées.

## 1. Scénario cible et propriétés non négociables

1. A ouvre l'application sur smartphone compatible AR, vise un mur, écrit « bonjour » ou dessine une ligne.
2. A voit son geste dans le flux de caméra, spatialement posé sur le mur (ou au sol, sur un objet stable, à une hauteur définie).
3. A sauvegarde. B arrive avec un **autre appareil**, quelques minutes, jours ou semaines plus tard, et voit l'inscription au **même endroit physique**, depuis un autre angle.
4. B peut marcher et tourner la tête : la ligne reste ancrée et ne flotte pas avec l'écran. Une personne située à un autre étage ne reçoit pas aveuglément toutes les inscriptions de la même latitude/longitude.
5. Au déplacement, l'application charge le contenu local utile, puis précharge les zones voisines ; elle ne télécharge jamais la collection mondiale.
6. La vision finale est **publique et partagée entre tous les utilisateurs de l'application**, pas un calque personnel ou une session multi-utilisateur éphémère. La confidentialité/modération et le droit à retrait restent obligatoires.

**Hors périmètre initial :** création artistique avancée, reconnaissance universelle de chaque surface, lunettes autonomes, écriture collaborative au même milliseconde, métavers complet, modélisation 3D de la Terre, IA générative, reproduction photographique fidèle du site, zones intérieures sans infrastructure de relocalisation.

**Question centrale :** comment convertir des coups de pinceau observés dans un référentiel AR éphémère en géométrie 3D durable, puis recalibrer fidèlement cette géométrie lorsqu'un autre utilisateur revient ?

## 2. État de l'art / projets ressemblants (repérage du 26-10-2026)

**Il existe déjà des analogues.** La nouveauté commerciale ou scientifique du concept n'est donc **pas démontrée**. Examiner sérieusement :

| Projet / système | Point commun | Question ouverte / limite à mesurer |
| --- | --- | --- |
| WallaMe (application lancée en 2015, depuis retirée du Play Store selon AppBrain) | Messages, dessins et surfaces géolocalisés visibles par d'autres utilisateurs | Qualité de reconstitution spatiale, plateforme désormais historique |
| Kanvio (site présentant des apps iPhone et Android) | Dessins et messages AR persistants sur des surfaces réelles | Vérifier indépendamment l'étendue effective, la précision inter-appareils et les conditions d'accès |
| Spray: AR & AI Graffiti Art (fiche App Store) | Graffiti AR, découverte des œuvres proches, ancrage et durée de publication | Examiner son modèle d'ancrage, l'exactitude 3D, la modération et les limites d'usage |
| Cospray (fiche de projet Devpost) | « Shared world canvas », peinture et géolocalisation collaboratives | Vérifier prototype, maturité, repos et reproductibilité ; ne pas supposer un déploiement mondial |
| Google ARCore Geospatial API | Ancrages WGS84 / terrain / toiture, Visual Positioning System basé sur des cartes visuelles | Couverture variable, précision contextuelle, accès, quotas, conditions de traitement des données |
| Niantic Spatial SDK 4.x / VPS | Relocalisation visuelle et ancrages persistants dans des zones cartographiées | Couverture locale, maturité SDK, contraintes plateforme, dépendance fournisseur |
| Apple ARKit GeoTracking | Geo-ancres en latitude, longitude et altitude | Fonctionnement extérieur et couverture géographique limitée |
| OGC GeoPose 1.0, OGC 3D Tiles | Standards pour échanges de poses et streaming géospatial | Ce sont des briques, **pas** des solutions complètes de relocalisation ni de graffiti |

**Point de vigilance 2026 :** les anciennes ressources Niantic Lightship / ARDK 3.x ne constituent plus une cible durable ; la documentation annonce l'arrêt de Shared AR en 3.x au 01-05-2026 et la migration vers le SDK 4.x. Revérifier les versions, conditions, quotas et prix au lancement de toute étude.

Sources à reconsulter et dater à chaque reprise :
- WallaMe : https://www.appbrain.com/app/wallame-augmented-reality/com.wallame
- Kanvio : https://kanv.io/
- Spray : https://apps.apple.com/us/app/spray-ar-ai-graffiti-art/id6743058938
- Cospray : https://devpost.com/software/fresco-b1riws
- Google Geospatial : https://developers.google.com/ar/develop/geospatial
- ARCore précision/limitations : https://developers.google.com/ar/reference/java/com/google/ar/core/Config.GeospatialMode
- Niantic Spatial (documentation actuelle) : https://nianticspatial.com/docs/nsdk/
- Niantic VPS : https://www.nianticspatial.com/docs/nsdk/4.3.0/features/lightship_vps/
- Apple GeoTracking : https://developer.apple.com/documentation/ARKit/ARGeoTrackingConfiguration
- OGC GeoPose : https://www.ogc.org/standards/geopose/
- OGC 3D Tiles : https://www.ogc.org/standards/3DTiles/

**Résultat du repérage :** ce projet doit se différencier par une **mesure rigoureuse de persistance spatiale multi-appareils, de rendu en 3D/altitude, de passage à l'échelle mondial et de gouvernance d'un calque public**, plutôt que par la seule idée de dessiner sur un mur.

## 3. Ce qui est faisable, difficile et non démontré

- **Probablement faisable avec matériel grand public en zone favorable :** gestes/toucher, tracé vectoriel, ancrages AR, affichage du voisinage, stockage serveur, partage entre appareils, géolocalisation 3D.
- **Difficile :** maintenir un trait au même centimètre sur différents téléphones, à différents moments, en marchant, selon les conditions de lumière, la météo, les changements de façade et la couverture de cartographie VPS.
- **Non démontré :** positionnement centimétrique partout sur la planète ou à tous les étages sans cartographie, instrumentation locale ou relocalisation visuelle suffisante.
- **Important :** le GPS seul ne résout ni la rotation fine, ni le placement sur un mur, ni une hauteur verticale fiable. ARCore indique une précision VPS typiquement meilleure que 5 m et souvent voisine de 1 m, **pas une garantie centimétrique universelle**. Niantic évoque des capacités centimétriques en lieux cartographiés et conditions favorables ; à **vérifier expérimentalement**.
- **Distinction obligatoire :** géolocalisation de découverte (quel site / quel quartier) ≠ recalage visuel fin de l'ancre (quelle brique / quel centimètre sur le mur) ≠ suivi local image par image (éviter la dérive en marchant).
- **Surtout :** l'altitude doit être normalisée. La hauteur ellipsoïdale WGS84, l'altitude orthométrique, la hauteur par rapport au sol et la hauteur « étage » ne sont pas interchangeables.

## 4. Questions de recherche falsifiables

**H1 — Persistance géométrique.** Une ancre partagée, recalée par VPS, permet à B de retrouver les traits dessinés par A avec une erreur quantifiée, sur un même mur, après fermeture/réouverture et depuis plusieurs angles. Comparer à GPS + boussole seuls.

**H2 — Persistance temporelle.** La qualité reste acceptable à J+1 et J+7, sous changements de luminosité et de météo ; mesurer les pires cas, échecs de localisation et repositionnements.

**H3 — Altitude et surfaces.** Un modèle 3D explicite évite les confusions entre un mur au rez-de-chaussée, sa partie haute et un autre étage. Comparer GPS 2D, altitude GPS/barométrique si disponible, ancre visuelle 6DoF, et filtre géométrique 3D.

**H4 — Passage à l'échelle.** L'indexation géographique + altitude + volumes d'intérêt + mise en cache apporte un chargement local presque indépendant du nombre total d'inscriptions sur Terre, **à densité locale et infrastructure comparables**. Le coût dépend d'abord du contenu dans le champ et à proximité, non de la superficie théorique de la planète.

**H5 — Fidélité représentation.** Stocker des polylignes 3D et leurs transformations sur la surface est plus robuste, redimensionnable et économique que stocker des captures d'écran. Comparer taille, compression, artefacts, recalage et fluidité.

**H6 — Fiabilité de longue durée.** Des ancres versionnées et éventuellement de nouvelles cartographies permettent de restaurer une inscription après changement du référentiel ou de la façade, ou au minimum de déclarer le contenu orphelin **sans l'afficher au mauvais endroit**.

**H7 — Viabilité sociale.** Une toile publique globale exige quotas, signalement, effacement, modération et prévention des abus avant ouverture libre ; comparer coût de modération et trafic à un pilote public non modéré (ce dernier **ne doit pas** être déployé).

**H8 — Dépendances.** Un format de stockage propre à l'application et une interface d'adaptateur de pose rendent possible le remplacement d'un fournisseur VPS ; vérifier une migration de relocalisation sans reconstituer toutes les œuvres.

## 5. Architecture théorique candidate (à challenger, pas à implémenter immédiatement)

### 5.1 Chaîne côté appareil

Capteurs caméra/IMU/GNSS -> moteur AR et suivi visuel-inertiel (SLAM/VIO) -> estimation pose 6DoF -> ancre globale/visuelle -> raycast vers plan/profondeur ou mesh de surface -> échantillons de trait localisés -> prévisualisation stable -> validation -> sérialisation compacte.

À la lecture : position approximative -> découverte des cellules proches -> téléchargement des métadonnées utiles -> résolution des ancres/transformations -> rendu spatial/occlusion -> filtrage du champ de vision et de la visibilité.

**Attention aux erreurs silencieuses :** ne pas accepter un trait comme géospatialement durable tant que l'état de relocalisation et l'incertitude de pose ne sont pas satisfaisants. Prévoir un mode « brouillon local / précision insuffisante ».

### 5.2 Référentiels et ancrage

1. Stocker une localisation globale WGS84 documentée, avec hauteur et référentiel vertical déclarés ; utiliser ECEF pour échange global et **ENU local** pour calculs de tracé proches d'une ancre.
2. Relier chaque trait à un **identifiant d'ancre de surface** versionné et à des points 3D locaux, ainsi qu'à une orientation/normale de surface lorsque pertinente. La transformation entre ancre et système global ne doit jamais être implicitement permanente.
3. Conserver incertitude de position/orientation, source de localisation (GPS, VPS, mapping privé), date et statut du référentiel. Un nouveau recalage pourra déplacer l'ancre sans réécrire chacun des points.
4. Utiliser des coordonnées flottantes en petit repère local pour éviter la perte de précision si le moteur 3D utilise du flottant 32 bits à l'échelle de la Terre.
5. Raycast/profondeur pour accrocher les traits au mur ; gérer occlusion et collisions, avec repli visuel explicite lorsque profondeur absente.
6. Comparer plusieurs stratégies : (A) ancrage global géospatial, (B) ancrage local VPS/Cloud Anchor et repère global grossier, (C) carte visuelle locale produite par les utilisateurs. Décider par les mesures, pas par l'effet marketing.

### 5.3 Modèle conceptuel minimal

**Anchor** : id stable, zone, provider/type, coordonnées globales et hauteur avec datum, transform / orientation, surface/normal, version, confidence/covariance, état, dates de validité.

**Stroke** : id, anchor_id/version de création, auteur pseudonyme interne, points de polyligne (x,y,z locaux quantifiés ou compressés), épaisseur, couleur, éventuellement text/typo, bounding box 3D, temps de création, état de visibilité/modération, version.

**Cell manifest** : id d'index 2D, tranche d'altitude éventuelle, version/ETag, compteurs, bounding volumes, ids/paquets voisins ; éviter doublons aux frontières.

**Events/tombstones** : créations et suppressions persistantes, journal minimal auditable, propagation des retraits aux caches. Des opérations immuables / CRDT ne seront étudiées qu'en cas d'édition simultanée réelle, pas par réflexe.

Le contenu textuel doit posséder son modèle (texte UTF-8 + police/licence + pose), non être automatiquement converti en image lourde. Les médias éventuels relèvent plus tard du stockage objet.

### 5.4 Indexation et diffusion

- Découverte : partition mondiale approximative 2D (H3, S2 ou quadtree), puis **sélection 3D réelle** (altitude/boîtes spatiales/index 3D ou octree sur zones denses). H3 est une grille **2D** : H3 seul **ne traite pas les étages** et ses cellules ne sont pas une géométrie d'inclusion exacte à toutes les résolutions.
- Stockage pilote : PostgreSQL + PostGIS (géométries et volumes 3D, index spatial) ; comparer les types géographiques/les projections et requêtes 3D au lieu de supposer qu'une simple colonne GPS suffit.
- API : requête de zone + altitude + rayon + version du manifeste, pagination et taille de charge plafonnées ; renvoyer uniquement les contenus actifs et autorisés.
- Appareil : cache LRU de tuiles et géométrie, deltas/ETag, purge des suppressions, préchargement des cellules devant la trajectoire ; viser performances sur connexions imparfaites.
- Rendu : frustum culling, distance/LOD, densité maximum par pixel/mur, occultation réaliste si profondeur disponible, budget FPS.
- Densités extrêmes : empaquetage de tuiles et représentation agrégée, mais **ne pas supprimer silencieusement des traits** à cause d'une surcharge.
- Multi-utilisateur : idempotence des créations, ordre de versions, anti-doublon, mises à jour différées et propagation des suppressions. Temps réel par push **optionnel** au début ; une actualisation courte peut suffire.
- Une architecture cloud mondiale, CDN, files de messages, sharding inter-régions et CRDT ne se justifient qu'après mesures du pilote. Un monolithe bien instrumenté est une hypothèse initiale raisonnable.

**Références :** H3 https://h3geo.org/docs/ ; PostGIS 3D https://postgis.net/docs/manual-3.7/en/ST_3DDWithin.html ; 3D Tiles https://www.ogc.org/standards/3DTiles/ . Ce dernier concerne surtout de volumineuses scènes 3D ; ne pas l'adopter automatiquement pour des polylignes légères.

### 5.5 Dimensionnement : ordres de grandeur, non benchmarks

Hypothèse illustrative : **1 000 000 de traits × 2 Ko/trait ≈ 2 Go de données brutes** (hors index, blobs d'ancres, modération, réplications et sauvegardes). L'estimation dépend énormément des points par trait, du format et des métadonnées. Un million de traits n'impliquent pas le chargement d'un million de traits sur chaque appareil.

La difficulté initialement pressentie comme « stockage mondial » est à étudier, mais la **précision inter-appareils, la couverture VPS, le coût de la relocalisation et la modération** risquent d'être plus contraignants au départ. Ne pas extrapoler le coût final d'un petit test sans modèles de trafic et de densité.

## 6. Matériel, plateformes et coûts à étudier

| Étape | Équipement minimum envisagé | Limite / test |
| --- | --- | --- |
| Simulation sans AR | Ordinateur ordinaire + base PostGIS + données synthétiques | Teste l'indexation, **pas** la fidélité dans la rue |
| Prototype réel mono-appareil | Smartphone Android compatible ARCore, GPS/caméra/IMU et connexion ; accès à un site extérieur sûr | Dessiner/retrouver sur même appareil |
| Démonstration de partage | **Deux téléphones** réellement indépendants (idéalement modèles distincts) ; même site ; serveur réseau simple | Test crucial de recalage multi-appareils |
| Comparaison de fournisseurs | Téléphone(s) compatibles avec les SDK retenus et zone avec couverture VPS vérifiée | Mesurer précision/couverture/coûts, notamment Google et Niantic |
| Recherche avancée facultative | Téléphone avec capteur de profondeur/LiDAR ou caméra de profondeur, cibles de mesure non permanentes | Décomposer erreur de profondeur et erreur de localisation |
| Plus tard | Lunettes AR/mixte avec SDK, accès capteurs, connexion et capacités de localisation adaptées | **Non exigées** pour prouver le concept |

Évaluer coûts fixes (serveur, stockage), coûts variables (VPS/API, sortie réseau, cartes, journalisation, modération, comptes), restrictions SDK, licences, région de traitement des images, verrou fournisseur. **Aucun matériel spécifique ni prix n'est imposé à cette étape.**

## 7. Protocole proposé, à exécuter après sortie de l'incubateur

> **Ce document n'atteste aucune expérimentation.** La bibliographie et les questions de cadrage peuvent rester ici. Dès la décision d'exécuter des essais P0-P5 (mesures de terrain, applications concurrentes, benchmarks, simulation de charge), ouvrir le dépôt projet, transférer le protocole et retirer cette fiche de l'incubateur. Les étapes ci-dessous décrivent alors le travail **du futur laboratoire autonome**.


**P0 — Bibliographie et test de disponibilité**
- Tester les apps comparables, relever date/version, plateformes, publication réelle, précision et caractère public/persistant.
- Vérifier couverture VPS de 2 à 3 sites candidats, quotas et conditions d'utilisation à date.
- Faire une matrice de décision ARCore Geospatial / Niantic Spatial VPS / ARKit GeoTracking / ancrage local cartographié ; inclure dépendance fournisseur et continuité de service.
- Définir le référentiel de vérité de mesure : repères physiques autorisés, distances connues, plan de façade / cibles non intrusives. Aucune publication du site exact dans ce dépôt public.

**P1 — Métrologie hors produit**
- Sur petite zone sûre (par exemple un segment de mur + 10 à 30 m de déplacement), relever la position réelle d'au moins 10 points de référence ; mesurer l'écart horizontal, vertical et la dérive dans le temps.
- A crée 20 traits, redémarre, revient sous 3 angles ; B (autre appareil) refait la même expérience. Répéter plusieurs fois, en conditions lumineuses différentes.
- Consigner moyenne, médiane, P95, décalage maximal, taux de relocalisation, dérive après marche, temps pour retrouver une ancre, causes d'échec. Comparer avec GPS seul et relocalisation VPS.
- Cibles de recherche **à confirmer, pas des performances promises** : médiane erreur de repositionnement ≤25 cm et P95 ≤75 cm sur façade cartographiée, relocalisation fiable dans ≥90 % des essais en conditions favorables ; toute dégradation doit être signalée à l'écran.

**P2 — Représentation/altitude**
- Confronter un trait au sol et un trait situé 2–3 m plus haut, puis un autre niveau d'un même bâtiment si accessible et autorisé.
- Comparer point unique, polyligne 3D ancrée, coordonnées globales par point, ancre de surface partagée ; normaliser explicitement hauteur/datum.
- Évaluer taille, continuité visuelle, rendu oblique, disparition derrière obstacle, résistance au changement de téléphone.

**P3 — Simulation d'échelle (sans foule ni déploiement public)**
- Générer 100 / 1 000 / 100 000 puis 1 000 000 traits synthétiques dans des répartitions uniforme et fortement concentrée.
- Comparer H3 seul, H3 + bandes de hauteur + PostGIS, index/volumes 3D plus fins si utile. Tester les frontières de cellules, les longs traits couvrant plusieurs cellules, les étages et la mise à jour des caches.
- Mesurer taille en base + index + sauvegardes, requêtes P50/P95/P99, coût de calcul, charge utile, pic mémoire client, latence d'apparition, FPS, réseau. Rejouer un trajet virtuel et plusieurs arrivées simultanées.
- Hypothèses de service à mesurer : données visibles depuis le cache en moins de 2 s, chargement de géométrie froide en moins de 5 s dans des conditions réseau déclarées, rendu ≥30 FPS sur appareil cible ; **le délai de localisation VPS est mesuré séparément**.

**P4 — Robustesse et gouvernance**
- Déconnexion, faible bande passante, perte/relocalisation d'ancre, erreur de hauteur, bâtiment modifié, contenu signalé, suppression et purge de cache.
- Tester des « écritures simultanées », quotas, anti-spam, rate limiting, dédoublonnage, version de référence et retour arrière.
- Évaluer RGPD/données de localisation, captation caméra par le SDK, politique de vie privée, droit d'effacement, contenus sensibles, propriété intellectuelle, sécurité dans la rue et règles de publication d'annotations sur lieux réels.

**P5 — Synthèse go / pivot / no-go**
- Rapport reproductible : données anonymisées, protocoles, échecs, intervalles d'incertitude, mesures, coûts estimés et comparaison concurrentielle.
- Décider *seulement alors* si le **laboratoire autonome déjà créé** doit devenir un produit, pivoter ou s'arrêter. Le dépôt dédié et le retrait de cette fiche de l'incubateur doivent avoir eu lieu **avant les expérimentations**, conformément aux règles du README.
- Si précision insuffisante : explorer cartes locales partagées, marqueurs visuels temporaires, fusion multi-session, incertitude explicite et cartographie participative. Ne jamais maquiller un échec de localisation en rendu « persistant ».

## 8. Arbitrages à réserver au chercheur

1. **Résultat scientifique prioritaire :** taux et précision de redécouverte par B, non nombre de fonctions de dessin.
2. **Plateforme :** Android ARCore pour un premier parcours *si couverture confirmée* ; comparer d'abord les fournisseurs, ne pas décider définitivement avant P0.
3. **Précision :** spécifier niveaux « exact/localisé », « approximatif » et « indisponible ». Un dessin mal aligné ne doit pas prétendre à une précision parfaite.
4. **Comportement dans le temps :** immortalité logique souhaitée ≠ immortalité technique absolue (services arrêtés, bâtiments détruits, réglementations, contenu retiré). Gérer les ancres périmées.
5. **Mode public :** visibilité partagée par défaut, mais contrôle anti-abus, suppression, signalement et gouvernance dès la conception. Politique de modération explicite ; possibilité de masquer des couches et zones sensibles.
6. **Recherche d'algorithmes nouveaux :** seulement si les SDK existants échouent sur une limite mesurée ; comparer SLAM/VIO et relocalisation visuelle ouverte (ex. ORB-SLAM3) en auditant licences, performances et confidentialité, sans reconstruire une cartographie planétaire inutilement.
7. **Gouvernance spatiale :** droits de pose sur lieux sensibles, bâtiments privés et espaces publics, visée ciblant des personnes, densité de graffitis, protection des mineurs et conflits d'annotations sont des difficultés de produit à part entière.

## 9. Critères de sortie de l'incubateur et passation à Codex

Le dossier **n'autorise aucune tâche de développement immédiate dans l'incubateur**. Le prochain travail souhaitable consiste à préparer la bibliographie P0 et un protocole P1 critiquable ; avant de commencer des tests réels, démarrer le projet dans son dépôt autonome. Le chercheur doit produire un inventaire sourcé, un tableau avantages/risques par SDK, des incertitudes, puis la grille de mesure. L'ingénieur code **après décision explicite de démarrer** et uniquement les expériences nécessaires.

À la création d'un véritable dépôt dédié (même uniquement de recherche), **retirer cette entrée et son lien de l'incubateur** ; transférer le document scientifique, les décisions, les mesures et l'historique projet dans le nouveau dépôt. Suivre AGENTS.md et docs/CHATGPT_PROJECT_HISTORY.md pour distinguer demandes exactes, résumés et travaux réellement réalisés.

---

**État des preuves au 26 octobre 2026 :** revue documentaire rapide uniquement, **aucun test d'application concurrente, de couverture VPS, de matériel, de performance ou de charge n'a été exécuté**. Toutes les métriques P1–P4 sont des critères de protocole proposés et doivent encore être validées.
