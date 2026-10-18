# Widget Android de qualité de l’air

Stade : **ancien prototype personnel**, distinct de l’application Android de liste de tâches.

[android-widget-lab](https://github.com/goldaj/android-widget-lab) conserve les sources Java de récupération d’un indice WAQI et d’affichage dans une activité et un widget.

Le jeton de l’ancienne configuration a été retiré de la copie publiée avant son premier commit et conservé dans un coffre local externe au dépôt. Un champ `BuildConfig` lit désormais une configuration de build privée.

Suites : remettre à niveau Gradle, Android SDK et les dépendances, restaurer le Gradle Wrapper manquant, remplacer `AsyncTask`, tester les erreurs réseau et le cycle de vie du widget. Pour une distribution, passer par un service intermédiaire afin que le token fournisseur ne soit pas embarqué dans un APK extractible.
