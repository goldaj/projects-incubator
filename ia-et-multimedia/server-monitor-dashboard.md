# Server Monitor Dashboard — voir si son serveur va bien

**Statut : concept d'outil, pas supervision déployée.** Cadrage enrichi le 2026-10-26 à partir d'une demande explicite de janvier 2026. Un ancien **prototype HTML à données simulées** a été évoqué ; ne pas le confondre avec un agent réellement opérationnel ni refaire un travail déjà versionné ailleurs.

## Besoin attesté
Un petit tableau de bord lisible pour savoir immédiatement si un serveur est **en ligne**, et comment évoluent ses ressources, sans naviguer dans cinq consoles. Les métriques demandées dans les échanges : CPU, mémoire, disque, flux réseau, journaux et alertes. Règles envisagées à l'origine : **avertissement au-delà de 80 % et critique au-delà de 90 %** pour certains taux d'occupation ; ces seuils ne conviennent pas uniformément à toutes les métriques.

## Scénarios utilisateurs
- J'ouvre la page : état global (disponible, dégradé, indisponible), date de la **dernière mesure**, ressources sous tension.
- Le serveur devient lent : je regarde CPU/RAM/disque, la tendance et les événements corrélés.
- Je cherche une erreur : filtrer les logs par plage de temps, niveau et mot-clé.
- Le réseau ou l'agent cesse de répondre : la page affiche « **mesures obsolètes / agent non joignable** » et non de fausses valeurs à zéro.

## Fonctions souhaitables
- Indicateurs CPU %, RAM utilisée/disponible, occupation par point de montage, I/O disque si collectable.
- Débit réseau entrant/sortant avec unités, fenêtre de mesure, éventuellement espace total et uptime.
- Historique court pour voir la tendance, sans prétendre qu'une pointe de 2 secondes représente l'usage de la journée.
- Alertes réglables avec délai de confirmation, hystérésis et retour à la normale pour éviter les alarmes en boucle.
- Logs paginés et recherche ; traitement explicite des champs sensibles.
- Horodatage, statut de collecte et distinction **démonstration / métrique réelle** toujours visibles.

## Architecture à évaluer
Deux composants possibles : collecteur local à privilèges minimaux → API authentifiée / stockage de séries temporelles léger → interface read-only. Commencer par un seul serveur et comparer collecte passive (Prometheus/node_exporter) ou petit agent spécifique. Éviter les commandes arbitraires à distance, la conservation infinie des logs et l'exposition directe des ports de métriques sur Internet.

La version d'essai peut simuler une panne CPU/réseau/logs pour valider l'UX ; **cela ne prouve pas** le bon fonctionnement sur un vrai serveur. Une fois sur VPS réel, prévoir HTTPS/VPN, authentification, chiffrement, gestion des secrets, quotas et journal d'accès.

## MVP hypothétique
Une page responsive, état + horodatage, quatre métriques principales, séries courtes, logs filtrables, seuils configurables et deux états simulés de panne. Puis **un seul connecteur réel** en lecture seule sur serveur de test. Évaluer charge CPU/RAM du moniteur, fraîcheur, exactitude et panne du collecteur.

## Frontière
Ne pas mélanger avec le **Twitch Streamer Dashboard**, qui vérifie le flux vu par les spectateurs. Surveiller un VPS ne prouve pas qu'une vidéo Twitch est correctement délivrée. Le projet trading ne doit jamais perdre de ressources critiques à cause de cet outil.

**À clarifier ultérieurement :** supervision du seul VPS, de plusieurs machines ou service grand public ; besoin de notifications et d'historique longue durée.
