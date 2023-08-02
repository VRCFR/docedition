
Ce document couvre les **composants**, **propriétés** et **événements de réseau** que vous pouvez utiliser dans vos programmes Udon.

## Propriétés de réseau

Propriétés spéciales que vous pouvez *obtenir* à partir du réseau :

- **IsClogged** - renvoie true s'il y a trop de données qui essaient de sortir. Vous pouvez utiliser ceci pour retarder certaines opérations ou ajuster votre logique.

- **IsInstanceOwner** - renvoie true si le joueur local est celui qui a créé l'instance. False lors des phases de construction et de test et en mode de lecture Unity.

- **IsMaster** - renvoie true si le joueur local est le "Maître" - soit la première personne qui a entré dans l'instance, soit la personne automatiquement désignée comme Maître lorsque le dernier Maître a quitté. Ancienne logique, non recommandée à utiliser. IsOwner devrait être utilisé à la place.

- **IsNetworkSettled** - renvoie true une fois que toutes les données de l'instance ont été désérialisées et appliquées, et qu'elle est prête à être utilisée.

- **LocalPlayer** - renvoie l'objet [API joueur VRC](/worlds/udon/joueurs) du joueur local. Sera nul dans l'éditeur - utilisez Utilities.IsValid pour facilement diviser votre logique en branches.

- **SimulationTime** - renvoie le temps de simulation actuel d'un joueur ou d'un objet avec des composants de réseau.
Le temps de simulation est un horodatage qui indique à quel point en arrière dans le temps un objet est simulé. Cette valeur est utilisée en interne pour [`VRCObjectSync`](/worlds/udon/composants-reseau/vrc-object-sync) et [joueurs](/worlds/udon/joueurs#simulationtime), mais peut également être utilisée dans les scripts Udon. Par exemple, si votre `Time.realtimeSinceStartup` est de 45 et que le SimulationTime d'un objet est de 44,5, alors VRChat croit qu'un délai de 500 ms est nécessaire pour reproduire en douceur l'objet à ce moment précis. Vous pouvez utiliser ce nombre pour obtenir des informations sur ce que `VRCObjectSync` fait, ou pour créer votre propre système similaire à `VRCObjectSync`. Par exemple, si vous faites `Time.realTimeSinceStartup - SimulationTime(joueur)` alors cela vous donnera exactement combien de latence ce joueur a à cet instant.
 
Le temps de simulation est fréquemment ajusté en fonction des conditions du réseau, comprenant de nombreux facteurs tels que la latence, la fiabilité et la fréquence des paquets reçus. L'objectif de cet ajustement est d'être aussi proche que possible du temps réel pour réduire la latence, mais de laisser suffisamment de marge pour éviter les accrochages. Il existe une variété de facteurs qui peuvent causer des accrochages, mais un exemple peut être de manquer de paquets reçus de la part du propriétaire.

## Événements de réseau

Ce sont les événements disponibles dans le système de réseau pour contrôler la synchronisation de vos données.

### OnPreSerialization :
Cet événement se déclenche juste avant que les données sérialisées soient envoyées, c'est un bon endroit pour définir les variables synchronisées que vous souhaitez mettre à jour pour les autres joueurs.

### OnDeserialization :
Cet événement se déclenche lorsque les données de synchronisation ont été transformées à partir des octets en variables utilisables. Il ne vous indique pas *quelles* données ont été mises à jour, mais sert de point de départ pour soit mettre à jour tout ce qui surveille les variables synchronisées, soit vérifier les nouvelles données par rapport aux anciennes données et effectuer des mises à jour spécifiques.

### OnDeserialization(DeserializationResult) :
Identique à OnDeserialization, mais avec des informations supplémentaires sur le moment où la demande a été envoyée et reçue.

#### DeserializationResult
`DeserializationResult` contient deux propriétés :
- `sendTime` : Le temps en secondes auquel ce message a été envoyé.
- `receiveTime` : Le temps en secondes auquel ce message a été reçu.

Les deux `sendTime` et `receiveTime` sont mesurés en fonction du temps en secondes depuis le démarrage de VRChat, depuis votre perspective (voir [Time.realtimeSinceStartup](https://docs.unity3d.com/ScriptReference/Time-realtimeSinceStartup.html)). Cela signifie que si vous voulez savoir il y a combien de secondes une certaine désérialisation a été envoyée, vous pouvez le calculer avec `Time.realtimeSinceStartup - sendTime`.

Notez que le `Time.realtimeSinceStartup` de chaque utilisateur est différent, donc le `sendTime` d'un joueur va être différent de celui d'un autre joueur. Par conséquent, si vous voulez synchroniser un `sendTime` spécifique avec d'autres joueurs, vous devrez calculer son décalage en soustrayant votre `Time.realtimeSinceStartup`. Ensuite, lorsque les autres joueurs reçoivent ce décalage, ils peuvent ajouter leur propre `Time.realtimeSinceStartup` au décalage pour déterminer le temps absolu par rapport à leur propre horloge.

SendTime peut être un nombre négatif si le message a été envoyé par quelqu'un d'autre avant que vous n'ayez jamais lancé VRChat.

### OnPostSerialization :
Cet événement se déclenche juste après une tentative d'envoi de données sérialisées. Il renvoie une structure **SerializationResult** avec un booléen 'success' et un entier 'byteCount' avec le nombre d'octets envoyés.

### OnSpawn :
Cet événement est obsolète - utilisez l'événement OnEnabled typique si vous souhaitez faire quelque chose lorsqu'un objet est "Spawned" à partir du pool.

### OnOwnershipRequest :
Cet événement est déclenché lorsqu'une personne demande à prendre la propriété. Il inclut les objets joueur pour le demandeur et le propriétaire demandé. Pour approuver ou refuser le changement, définissez une valeur booléenne dans un nœud "Set Return Value". Cette logique s'exécute localement à la fois sur le demandeur et le propriétaire, donc soyez conscient que des désaccords de logique entre les deux causeront une désynchronisation. Il est très probable que cela se traduise par le rejet inattendu du transfert de propriété par le propriétaire.

### OnOwnershipTransferred :
Cet événement est déclenché pour tout le monde dans l'instance lorsque la propriété d'un objet est modifiée, et comprend l'objet joueur pour le nouveau propriétaire.

### OnVariableChanged :
Il s'agit d'un type spécial d'événement que vous pouvez créer pour n'importe quelle variable. Dans le graphique Udon, vous le créez en faisant glisser-déposer une variable dans le graphique tout en maintenant la touche Alt enfoncée. Cet événement détecte lorsque la variable change, ce qui peut inclure lorsque vous recevez des variables synchronisées provenant d'autres joueurs. 
* Le changement du contenu d'un tableau ne déclenche pas de changement, car le tableau lui-même est toujours le même.
* OnVariableChanged se déclenche immédiatement lorsque la variable elle-même est écrite, contrairement à OnDeserialization qui se déclenche après avoir terminé l'écriture de toutes les variables synchronisées. Cela signifie que si vous utilisez OnVariableChanged à partir d'une variable synchronisée et essayez d'obtenir le contenu d'une autre variable synchronisée, il n'est pas garanti qu'elle a été mise à jour avec les dernières données synchronisées.

# VRC Object Sync
Ce composant synchronisera automatiquement la transformation (position, rotation échelle) et le rigidbody (physique) de l'objet sur lequel vous l'ajoutez. Il dispose de quelques méthodes et propriétés spéciales auxquelles vous pouvez accéder :

#### FlagDiscontinuity
Déclenchez ceci lorsque vous souhaitez téléporter l'objet - les modifications que vous apportez à cette image seront appliquées sans lissage.

#### Set/Get Gravity
Lorsque la gravité est activée, ce rigidbody est affecté par la gravité et tombera au sol. Normalement, la gravité est une propriété du rigidbody. Cependant, lorsque vous avez VRCObjectSync, cette propriété doit être contrôlée par le composant VRCObjectSync. Vous pouvez utiliser ces fonctions pour cela. Cela se comporte efficacement comme une variable synchronisée, donc **seul le propriétaire peut définir la gravité**.

#### Set/Get Kinematic:
Lorsque la cinématique est activée, ce rigidbody ignore les forces, les collisions et les joints. Normalement, la cinématique est une propriété du rigidbody. Cependant, lorsque vous avez VRCObjectSync, cette propriété doit être contrôlée par le composant VRCObjectSync. Vous pouvez utiliser ces fonctions pour cela. Cela se comporte efficacement comme une