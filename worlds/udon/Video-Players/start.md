

# Utilisation des préfabriqués

La manière la plus simple d'ajouter un lecteur vidéo dans votre monde Udon est d'utiliser l'un des préfabriqués que vous pouvez trouver dans `Assets/VRChat Examples/Prefabs/VideoPlayers`.

![Les deux préfabriqués de lecteur vidéo, prêts à être intégrés dans votre monde.](/img/worlds/video-players-aae04e6-video-player-prefabs.png)

Ces deux préfabriqués joueront une vidéo de votre choix, synchronisée pour tous les utilisateurs de votre monde. Elles ne boucleront pas - le graphe désactive la boucle pour obtenir une synchronisation. Si vous souhaitez qu'elles bouclent, activez 'Loop' et supprimez le comportement Udon.

:::note **Il s'agit d'EXEMPLES de lecteur synchronisé**

Vous n'êtes pas obligé d'utiliser les comportements "UdonSyncPlayer". Vous pouvez simplement utiliser le composant "VRC Video Player" si vous n'avez pas besoin de synchroniser les vidéos dans votre monde. Vous pouvez également créer vos propres graphes de synchronisation en utilisant le graphe fourni comme point de départ ou en le créant de zéro.

:::

# Choisir entre AVPro et Unity Video Player

Pourquoi choisir l'un ou l'autre ?
**AVPro** prend en charge les flux en direct sur plusieurs plateformes, comme YouTube Live, Twitch et quelques autres ! Vous devrez créer un graphe qui appelle "PlayURL" sur le lecteur vidéo pour que cela fonctionne. Le lecteur vidéo **Unity** ne prend pas en charge ces flux en direct.

De plus, le lecteur **AVPro** ne fonctionne pas dans l'éditeur - vous devrez construire et tester votre monde pour le voir fonctionner. Le lecteur vidéo **Unity** fonctionne en mode lecture dans l'éditeur lorsque vous utilisez des liens qui pointent directement vers des types de fichiers vidéo pris en charge tels que 'mp4' et 'webm'. Les services d'hébergement tels que YouTube et Vimeo ne fonctionneront que dans le client.

Il est important de noter que le composant haut-parleur AVPro implique la prise en charge de l'audio 8 canaux. Ce n'est pas correct - seul l'audio 6 canaux (généralement un audio 5.1) peut être lu. [AVPro prend en charge l'audio EAC3 7.1 uniquement sur PCVR]

# Compatibilité Android / Quest

VRChat sur Quest peut lire des vidéos à partir de liens directs vers des fichiers vidéo. Ces URL se terminent généralement par un nom de fichier correspondant à un type de vidéo pris en charge, comme http://quelquechose.com/video.mp4 ou http://test.com/chats.webm. Si vous visitez le lien et voyez tout un site web autour d'une vidéo, ce lien ne fonctionnera probablement pas sur Android / Quest car l'application que VRChat utilise pour résoudre ces liens en vidéos ne fonctionne pas sur Android. Les créateurs devront déplacer la vidéo vers un hébergeur prenant en charge les liens directs ou trouver un autre moyen de contourner ce problème.

Certains contournements existent pour les utilisateurs avancés. VRChat n'a pas examiné ces méthodes, ne les approuve pas et ne peut garantir leur fonctionnement continu, mais elles ont été recommandées par la communauté :

- [Streamlink](https://streamlink.github.io)
- [Publication d'Architechanon "Compréhension des URL dans VRChat"](https://ask.vrchat.com/t/protv-by-architechanon-usage-guides-and-walkthroughs/7029/11)

# Limitation de taux
Un utilisateur donné n'est autorisé à gérer une nouvelle URL de lecteur vidéo qu'une fois toutes les cinq secondes. Il s'agit d'une limite globale pour tous les lecteurs vidéo. Cela s'applique aux URL par défaut ainsi qu'à celles définies avec LoadURL et PlayURL.

Avec un seul lecteur vidéo, cela ne pose pas de problème - mais si vous avez plusieurs lecteurs vidéo, vous devez vous assurer de ne pas envoyer trop rapidement une demande après une demande précédente.

Cela s'applique également aux rejoins tardifs. Si vous avez 2 lecteurs vidéo en marche dans votre monde, un utilisateur dont l'arrivée est tardive verra qu'il doit envoyer deux demandes vidéo. Si cela n'est pas géré, il tentera de le faire simultanément et échouera. Dans les cas où vous avez plusieurs lecteurs vidéo jouant simultanément dans un monde, vous devrez en tenir compte.

# Hébergeurs vidéo pris en charge
Pour lire une vidéo, vous devez fournir une URL dans le champ URL de la vidéo lorsque vous configurez votre lecteur vidéo dans l'éditeur, ou vous pouvez coller une URL dans le champ VRCUrlInputField fourni dans les préfabriqués.

Une liste complète de nos hébergeurs pris en charge est disponible à l'adresse [Video Player Whitelist](/worlds/udon/video-players/www-whitelist). Voici quelques recommandations.
:::note Avertissement

*Les listes ci-dessous ne constituent pas des partenariats ou des recommandations*. Ce sont des services largement accessibles et qui ont été testés pour fonctionner correctement avec les lecteurs vidéo VRChat.
:::

### Votre propre hébergeur

- **Coût** : Payant - varie en fonction de votre fournisseur
- **Liens** : Lien directement vers le fichier .mp4 ou .webm
- **Limitations** : Si vous avez votre propre hébergeur en dehors de notre liste blanche, les utilisateurs doivent activer l'option "Autoriser les URL non fiables" dans leurs paramètres pour voir votre contenu.

Vous voudrez peut-être envisager d'utiliser un "réseau de diffusion de contenu" (CDN) pour héberger votre contenu. Cela est utile si vous prévoyez que votre vidéo sera accessible à de nombreux utilisateurs, ou pour qu'elle soit rapide pour de nombreux utilisateurs à travers le monde. Les CDN distribueront votre fichier sur de nombreux serveurs à travers le monde pour garantir qu'il y ait une source proche du spectateur afin de garantir des téléchargements rapides.

Nous avons testé *Amazon Cloudfront* et *BunnyCDN*. Les services de CDN sont généralement payants, mais ils sont peu coûteux pour le stockage/transmission en masse de données. Cependant, en raison de leur ouverture, ils ne sont pas présents dans notre liste blanche et nécessiteront que les utilisateurs activent l'option "Autoriser les URL non fiables".

### YouTube
- **Coût** : Gratuit
- **Liens** : Utilisez l'URL ['watch'](https://www.youtube.com/watch?v=8yaQY0arCnc)
- **Limitations** : Ne fonctionnera pas sur Quest ni sur Linux

### Vimeo Basic
- **Coût** : Gratuit
- **Liens** : Utilisez l'URL [de la vidéo basique](https://vimeo.com/383935156)
- **Limitations** : Ne fonctionnera pas sur Quest ni sur Linux

### Vimeo Pro ou Business
- **Coût** : [Payant](https://vimeo.com/upgrade)
- **Liens** : Utilisez les liens directs vers la vidéo
- **Limitations** : Aucune

### Optimiser vos vidéos
Lors de l'encodage de vos vidéos, nous vous recommandons vivement de télécharger une version optimisée pour le web. Pour les fichiers `.MP4`, cette option est également connue sous le nom de 'démarrage rapide'. Il s'agit d'un paramètre à cocher qui fait une énorme différence dans la possibilité de diffuser un fichier vidéo auto-hébergé. Sans démarrage rapide, vous devez généralement télécharger l'intégralité du fichier vidéo pour le lire. Avec le démarrage rapide activé, vous pouvez diffuser le fichier vidéo par morceaux, et les flux commenceront immédiatement.

- Dans FFMPEG, utilisez le paramètre `-movflags +faststart`.
- Dans HandBrake, cochez la case "Optimisé pour le Web".
- D'autres logiciels devraient avoir des options similaires pour activer le démarrage rapide.

![Activation du démarrage rapide](/img/worlds/video-players-dc8e54f-image.png)