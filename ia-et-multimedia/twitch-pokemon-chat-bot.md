# Bot Twitch de commandes de jeu

**Stade : prototype Python historique, versions modulaire et monofichier.**

Le projet explore lecture du chat Twitch, commandes, orchestration asynchrone et envoi de touches vers une fenêtre d'émulateur. Il dispose aussi d'un utilitaire OAuth manuel. Les sources propres sont conservées dans le dépôt privé `twitch-pokemon-chat-bot` ; aucune ROM ni distribution d'émulateur n'y est ajoutée.

Les jetons et comptes sont chargés depuis un coffre local. Le flux OAuth préparé ne doit pas imprimer de jetons. La préparation n'a connecté aucun compte et n'a envoyé aucune frappe à une application.

Prochaines étapes : fixer la version TwitchIO, tester hors réseau le cycle OAuth, les limites de fréquence et l'annulation, protéger la sélection de fenêtre et fournir un arrêt local explicite. Une variante Processing distincte reste une source locale à qualifier plutôt qu'une réalisation dupliquée.
