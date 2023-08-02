

String Loading vous permet de télécharger des fichiers texte depuis internet et de les utiliser dans votre monde VRChat. Vous pouvez soit utiliser le script `DownloadString` inclus dans le SDK, soit créer votre propre script en utilisant la nouvelle fonction `VRCStringDownloader.LoadUrl`.

* Une chaîne de caractères peut être téléchargée toutes les cinq secondes. Si cette limite est dépassée, les téléchargements de chaînes de caractères sont mis en file d'attente et téléchargés dans un ordre aléatoire.
* Une chaîne de caractères ne peut pas dépasser 100 Mo.
* Vous ne pouvez avoir que 1000 éléments dans la file d'attente.

# URLs de confiance
Si un site ne figure pas dans la liste, il ne sera pas téléchargé à moins que l'option "Autoriser les URLs non fiables" ne soit activée dans les paramètres de l'utilisateur.

Les URLs suivantes sont disponibles :

* GitHub (`*.github.io`)
* Pastebin (`pastebin.com`)
* Github Gist (`gist.githubusercontent.com`)

# Guides
## Utilisation du script `DownloadString` pour télécharger une chaîne de caractères
Le SDK inclut un script pour télécharger facilement des chaînes de caractères :

1. Créez un nouvel objet GameObject dans votre scène.
2. Ajoutez un composant `UdonBehaviour`.
3. Sélectionnez `DownloadString` comme source de programme.
4. Entrez l'URL et sélectionnez le composant de texte où vous souhaitez afficher le texte téléchargé.

## Créer votre propre script pour LoadUrl
Vous pouvez utiliser la fonction `VRCStringDownloader.LoadUrl` pour télécharger des chaînes de caractères dans vos propres graphiques.

1. Exécutez `VRCStringDownloader.LoadUrl` avec une URL et spécifiez un UdonBehaviour.
2. Attendez que l'événement `OnStringLoadSuccess` ou `OnStringLoadError` soit appelé sur l'UdonBehaviour spécifié.
3. Utilisez l'interface `IVRCStringDownload` de l'événement pour obtenir le résultat du téléchargement de la chaîne de caractères.

# Nouveaux nœuds UdonGraph
## Nouveaux événements
### OnStringLoadSuccess
Renvoie `IVRCStringDownload`. Appelé lorsque la fonction `LoadUrl` a téléchargé avec succès la chaîne de caractères depuis internet.

### OnStringLoadError
Renvoie `IVRCStringDownload`. Appelé lorsque la fonction `LoadUrl` a échoué dans le téléchargement de la chaîne de caractères.

## Nouveaux types
### VRCStringDownloader

Utilisez cette classe statique pour télécharger des chaînes de caractères depuis le web.

#### VRCStringDownloader.LoadUrl
* **Url** : l'URL à charger depuis internet.
* **UdonBehaviour** : l'UdonBehaviour vers lequel envoyer les événements.
    * Dans Udon Graph, cela est par défaut l'UdonBehaviour actuel.
    * Dans Udon Sharp, vous pouvez utiliser `(IUdonEventReceiver)this`

### IVRCStringDownload
Résultat des événements de téléchargement des chaînes de caractères.

* **GetError (`string`)** : Le message d'erreur pour `OnStringLoadError`.
* **GetErrorCode (`int`)** : Le code d'erreur HTTP pour `OnStringLoadError`.
* **GetResponse (`string`)** : La chaîne de caractères qui a été téléchargée.
* **GetUdonBehaviour (`UdonBehaviour`)** : L'UdonBehaviour vers lequel les événements sont envoyés.
* **GetUrl (`VRCUrl`)** : Obtient l'URL à partir de laquelle le téléchargement a été tenté.