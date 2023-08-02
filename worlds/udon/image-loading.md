

Le chargement d'images vous permet de télécharger des images depuis Internet et de les utiliser comme textures dans vos matériaux. L'API inclut un script facile à utiliser appelé `ImageDownload`, ou vous pouvez créer votre propre script avec le nouvel objet `VRCImageDownloader`.

- La résolution maximale est de 2048 × 2048 pixels.
  - Tenter de télécharger des images plus grandes entraînera une erreur.
- Une image peut être téléchargée toutes les cinq secondes.
  - Si cette limite est dépassée, les téléchargements d'images sont mis en file d'attente et téléchargés dans un ordre aléatoire.
  - Cette limite s'applique à l'ensemble de votre scène, quelle que soit la quantité de composants VRCImageDownload utilisés.
- L'URL doit pointer directement vers un fichier image.
  - La redirection d'URL n'est pas autorisée et entraînera une erreur.
- Les images téléchargées sont automatiquement interprétées comme des images RGBA, RGB ou RG.
  - Par exemple, une image en niveaux de gris avec un canal alpha est interprétée comme une image RG.
- Il y a une limite de 1000 éléments dans la file d'attente.
- Les tampons d'entrée et de sortie sont limités à un maximum de 32 Mo, les images dépassant cette taille entraîneront une erreur.

## URLs de confiance

Les domaines suivants sont autorisés à être utilisés avec le chargement d'images. Si un domaine n'est pas dans la liste, les images ne se téléchargeront pas à moins que l'option « Autoriser les URLs non fiables » ne soit activée dans les paramètres de l'utilisateur.

- Discord (`cdn.discordapp.com`)
- Dropbox (`dl.dropbox.com`)
- GitHub (`*.github.io`)
- ImageBam (`images4.imagebam.com`)
- ImgBB (`i.ibb.co`)
- imgbox (`images2.imgbox.com`)
- Imgur (`i.imgur.com`)
- Postimages (`i.postimg.cc`)
- Reddit (`i.redd.it`)
- Twitter (`pbs.twimg.com`)
- VRChat (`assets.vrchat.com`)

## Guides

### Utiliser le script `ImageDownload` pour télécharger une image

L'API inclut un script pour télécharger facilement des images :

1. Créez un nouvel objet dans votre scène.
2. Ajoutez un composant UdonBehaviour.
3. Sélectionnez `ImageDownload` comme source du programme.
4. Sélectionnez un matériau pour appliquer la texture téléchargée.
5. (Optionnel) Personnalisez `TextureInfo` pour modifier les paramètres de la texture téléchargée.

### Créez votre propre script pour `VRCImageDownloader`

Vous pouvez utiliser `VRCImageDownloader` dans vos propres scripts Udon Graph. Voici comment faire :

1. Créez un nouvel objet `VRCImageDownloader` avec son nœud Constructeur.
2. Enregistrez le nouveau `VRCImageDownloader` créé en tant que variable (cela est **obligatoire**, voir « Remarques »).
3. Exécutez la fonction `DownloadImage` sur l'instance `VRCImageDownloader`.
4. (Optionnel) Attendez que l'événement `OnImageLoadSuccess` ou `OnImageLoadFailure` soit exécuté.

## Nœuds UdonGraph

### Nœuds de type

#### VRCImageDownloader

Utilisez le constructeur de `VRCImageDownloader` pour créer un téléchargeur d'images, qui peut télécharger des images depuis Internet en temps d'exécution.

##### DownloadImage

Télécharge une image et appelle un événement indiquant la réussite ou l'échec (voir « Nouveaux événements »).  
Renvoie un `IVRCImageDownload` qui peut être utilisé pour suivre la progression du téléchargement.

- **Instance** : Le composant `ImageDownloader` pour télécharger l'image avec.
- **Url** : L'URL `VRCURL` de la texture à télécharger.
- **Material** (optionnel) : Le matériau auquel appliquer automatiquement l'image téléchargée, en tant que texture principale.
- **UdonBehavior** (optionnel) : Le `UdonBehavior` auquel envoyer les événements du `VRCImageDownloader`. Si `udonBehavior` est vide, le `UdonBehaviour` actuel recevra tous les événements.
  - Notez que UdonSharp ne recevra aucun événement à moins que `udonBehavior` ne soit spécifié.
- **TextureInfo** (optionnel) : L'objet `TextureInfo` contenant les paramètres de la texture nouvellement créée.

##### Dispose

Nettoie le `VRCImageDownloader`. Libère les textures téléchargées de la mémoire.  
(Appeler `Dispose` invalide l'objet `VRCImageDownloader` et il doit être réinstancié pour télécharger de nouvelles images).

###### Note concernant la mise au rebut et la collecte des déchets

- Appeler `Dispose` invalidera le `VRCImageDownloader`, l'`IVRCImageDownload` associé et la texture téléchargée.
  - Après avoir appelé `Dispose`, l'état `VRCImageDownloadState` de `IVRCImageDownload` passera à « Unloaded » jusqu'à ce qu'il soit récupéré par le ramasse-miettes.
- Le `VRCImageDownloader` conserve les textures en mémoire jusqu'à ce qu'il soit détruit ou supprimé à l'aide de la fonction `Dispose`.
- Assurez-vous de sauvegarder la référence de votre `VRCImageDownloader` en tant que variable pour éviter qu'il (et toute texture téléchargée) ne soit supprimé au hasard par le ramasse-miettes.

#### TextureInfo

Contient des paramètres à appliquer à une texture téléchargée.

- **GenerateMipmaps** : Active la génération de mipmaps. (Par défaut : `false`)
- **FilterMode** : Définit le `FilterMode` de la texture. (Par défaut : `Bilinear`)
- **WrapModeU** : Le `TextureWrapMode` le long de l'axe U (horizontal) (Par défaut : `Repeat`)
- **WrapModeV** : Le `TextureWrapMode` le long de l'axe V (vertical) (Par défaut : `Repeat`)
- **WrapModeW** : Le `TextureWrapMode` le long de l'axe W (profondeur, uniquement pertinent pour Texture3D). (Par défaut : `Repeat`)
- **AnisoLevel** : Le `anisoLevel` de la texture. Une valeur de 0 désactive le filtrage, 16 correspond à un filtrage complet. (Par défaut : `9`)
  - VRChat utilise un filtrage anisotrope forcé. Lorsque la valeur de `anisoLevel` est comprise entre 1 et 9, Unity fixe `anisoLevel` à 9. Si la valeur est supérieure à 9, Unity la fixe entre 9 et 16.
- **MaterialProperty** : Remplace la « MaterialProperty » à laquelle appliquer la texture téléchargée, si un « material » a été spécifié dans `DownloadImage`. (Par défaut : `_MainTex`)

#### IVRCImageDownload

Contient des informations sur l'image téléchargée. Renvoyé par la fonction `DownloadImage` de `VRCImageDownloader`, par `OnImageLoadSuccess` et par `OnImageLoadError`.  
Notez que bon nombre de ces champs seront invalides jusqu'à ce que le téléchargement soit terminé ou ait échoué.

- **Get Error** : Récupère l'« VRCImageDownloadError » associée à l'événement.
- **Get Errormessage** : Récupère le message d'erreur en tant que `string`.
- **Get Material** : Récupère le matériau envoyé dans la fonction `DownloadImage`.
- **Get Progress** : Récupère la progression du téléchargement de l'image en tant que `float` entre 0 et 1. Utilisez cela pour suivre la progression du téléchargement, par exemple pour des barres de chargement personnalisées.
- **Get Result** : La « Texture2d » de l'image téléchargée.
- **Get SizeInMemoryBytes** : Récupère la taille de la texture en octets en tant qu'`int`.
- **Get State** : Récupère le `VRCImageDownloadState` indiquant l'état du téléchargement de l'image.
- **Get TextureInfo** : Les informations de texture données à la fonction DownloadImage (TextureInfo)
- **Get Udonbehavior** : Récupère le comportement Udon donné où les événements de téléchargement d'image sont envoyés (UdonBehavior)
- **Get URL** : Récupère l'URL `VRCURL` du téléchargement de l'image.

#### VRCImageDownloadState

Indique l'état du téléchargement de l'image dans `IVRCImageDownload` :

- **Pending** : Pas encore commencé ou en cours.
- **Error** : Erreur de téléchargement (voir « VRCImageDownloadError »).
- **Complete** : Téléchargement terminé, la texture est prête à être utilisée.
- **Unloaded** : En attente