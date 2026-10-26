# Laboratoire IPTV personnel — comprendre et héberger sa télévision IP

**Statut : idée technique à démarrer.** Curiosité personnelle, non commerciale. « IPTV personnel » signifie ici **diffuser ou agréger des contenus pour lesquels on dispose des droits**, jamais contourner des abonnements ou distribuer des chaînes piratées.

## Objectif
Comprendre toute la chaîne d'une télévision sur IP en montant son propre environnement : source autorisée → capture/réception → encodage/packaging → catalogue de programmes → serveur → lecture sur téléphone, TV ou navigateur → télémétrie. Étudier **ce que l'on héberge réellement** : plateforme de lecture, serveur de flux personnel ou simple agrégateur.

## Cas d'usage de démonstration
- Diffuser en réseau local des vidéos personnelles et une chaîne « 24 h sur 24 » constituée de médias sous licence adaptée.
- Lire des chaînes gratuites **lorsque leur licence autorise explicitement** cette consommation/redistribution technique, ou des flux de démonstration publiés pour les tests.
- Construire un guide de programmes EPG synthétique, une playlist M3U personnelle, contrôle de lecture et reprise.
- Comparer un fonctionnement LAN isolé avec un accès distant sécurisé (si les droits et les ressources le permettent).

## Périmètre MVP
1. Déployer un petit serveur local avec une source de test que l'on contrôle.
2. Exposer un flux HLS simple et un catalogue clair ; lire depuis deux appareils.
3. Mesurer latence bout-en-bout, redémarrage, buffering, débit, transcodage et consommation CPU/GPU.
4. Ajouter une interface minimale de choix des chaînes et un guide fictif.
5. Automatiser la vérification des sources et l'arrêt propre.

## Alternatives et hypothèses d'architecture
- **Assembler** : FFmpeg pour média, nginx/Caddy pour HTTP, lecteur compatible HLS, stockage local. À comparer avec Jellyfin, Tvheadend, ErsatzTV et les architectures existantes ; **ne pas recréer un serveur de télévision complet sans raison**.
- Transcodage à la demande vs fichiers/segments pré-encodés ; HLS vs MPEG-TS, multicast LAN éventuellement.
- Sécurité : authentification hors LAN, limites de trafic, TLS, protection des appareils domestiques, surveillance, quotas, traces minimales.

## Points à vérifier avant d'aller plus loin
Droits d'auteur, droits voisins et conditions exactes de chaque flux ; accès IPTV de fournisseur personnel ≠ droit de redistribuer ce flux. En France, ne pas fournir de listes de chaînes piratées, accès illicites ou contournement DRM. Vérifier contraintes de réseau (NAT, IPv6, débit montant), encodage des appareils et éventuelles restrictions du matériel.

## Critères de réussite / sortie
Lecture stable de deux appareils, journal reproductible, mesure des ressources, documentation de la chaîne de bout en bout ; aucune chaîne non autorisée. Dès le premier labo effectivement exécuté, créer un dépôt dédié et retirer cette fiche de l'incubateur.

## Questions ouvertes
Veut-on une **chaîne personnelle** (type TV linéaire), un lecteur universel ou un serveur TV avec EPG/enregistrement ? Priorité LAN ou extérieur ? Source vidéo personnelle disponible ? Aucun de ces choix n'est tranché.
