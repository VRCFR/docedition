

:::note

VRChat sur Quest peut lire des vidéos à partir de liens directs vers des fichiers vidéo. Ces URL se terminent généralement par un nom de fichier se terminant par un type de vidéo pris en charge, tel que http://something.com/video.mp4 ou http://test.com/cats.webm. Si vous visitez le lien et que vous voyez tout un site web autour d'une vidéo, ce lien ne pourra probablement pas être lu sur Android / Quest car l'application que VRChat utilise pour résoudre ces liens en vidéos ne fonctionne pas sur Android. Les créateurs devront déplacer la vidéo vers un hébergeur prenant en charge les liens directs ou trouver un autre moyen de contourner ce problème.

Des solutions de contournement existent pour les utilisateurs avancés. VRChat n'a pas examiné ces méthodes, ne les approuve pas et ne peut pas garantir leur bon fonctionnement, mais elles ont été recommandées par des modifications suggérées de notre documentation.

* [Streamlink](https://streamlink.github.io)
* [Article "Comprendre les URLs dans VRChat" d'ArchiTechAnon](https://ask.vrchat.com/t/protv-by-architechanon-usage-guides-and-walkthroughs/7029/11)",

:::

Les services suivants sont sur la liste blanche du lecteur vidéo.

Si un service ne figure pas sur cette liste, il ne fonctionnera pas à moins que "Autoriser les URL non fiables" ne soit coché dans les paramètres.

VRChat sur Android ne lira pas de vidéo si l'hôte n'utilise pas le protocole HTTPS.

:::caution[Attention]

Le lecteur vidéo d'exemple dans le SDK ne gère pas les cas où le propriétaire a désactivé les "URL non fiables", ce qui empêchera la lecture des vidéos. Les créateurs de lecteurs vidéo créés par les utilisateurs peuvent modifier le code Udon pour confier la propriété de synchronisation à l'utilisateur demandant la vidéo.
:::

## Services autorisés
Les services énumérés ci-dessous sont intrinsèquement dignes de confiance et sont autorisés avec notre liste blanche d'URL par défaut. La ressource en cours d'accès (c'est-à-dire l'URL que vous entrez/utilisez dans le lecteur vidéo) doit résider dans le domaine du service indiqué à côté du nom du service. Cela signifie que les liens courts peuvent ne pas fonctionner !

:::note

*Les listes ci-dessous ne constituent pas des partenariats ou des recommandations et peuvent changer à tout moment sans préavis*.
:::

| Paramètre | Description |
| --- | --- |
| Soundcloud | `soundcloud.com` |
| FacebookVideo | `facebook.com` |
| NicoNico | `*.nicovideo.jp` |
| Twitch.TV | `*.twitch.tv` |
| Vimeo | `*.vimeo.com` |
| Youku | `*.youku.com` |
| YouTube | `*.youtube.com`,`youtu.be` |
| Mixcloud | `mixcloud.com` |
| VRCDN | `*.vrcdn.live`,`*.vrcdn.video` |