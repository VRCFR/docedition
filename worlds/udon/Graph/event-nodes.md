

Voici une liste de nœuds Udon considérés comme des "événements".

Les événements sont utilisés pour détecter des actions et déclencher des chaînes d'actions ou de logique. Les [événements d'entrée](/worlds/udon/input-events) ont leur propre page spéciale. Pour accéder à un événement dans le graphique, cliquez dessus dans la barre latérale du graphique.

Tous les nœuds ci-dessous ont des nœuds de flux lorsque la logique l'exige.

### Interact
Déclenché lorsque qu'un joueur de VRChat interagit avec cet objet.

### OnDrop
Déclenché lorsque qu'un joueur de VRChat lâche cet objet après l'avoir tenu.

### OnOwnershipTransferred
Déclenché lorsque la propriété de cet objet est transférée par un mécanisme quelconque.

### OnPickup
Déclenché lorsque cet objet est ramassé par un joueur de VRChat.

### OnPickupUseDown
Déclenché lorsque cet objet est tenu et que le bouton "Utiliser" est enfoncé. Se déclenche à l'appui du bouton.

### OnPickupUseUp
Déclenché lorsque cet objet est tenu et que le bouton "Utiliser" est enfoncé. Se déclenche au relâchement du bouton.

### OnPlayerJoined
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché lorsque qu'un joueur de VRChat rejoint l'instance. Envoie le `joueur` qui a rejoint.

### OnPlayerLeft
`Event_OnPlayerLeft`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché lorsque qu'un joueur de VRChat quitte l'instance. Envoie le `joueur` qui a quitté.

### OnSpawn
`Event_OnSpawn`
Déclenché lorsque cet objet apparaît pour le joueur local. Non mis en mémoire tampon, donc les joueurs rejoignant tardivement ne reçoivent pas cet événement. Se déclenche uniquement lorsque l'objet est créé via une instanciation réseau. Ne se déclenche pas si l'objet est présent dans la scène de base.

### OnStationEntered
`Event_OnStationEntered`
Déclenché lorsque qu'un joueur de VRChat entre dans la station sur cet objet.

### OnStationExited
`Event_OnStationExited`
Déclenché lorsque qu'un joueur de VRChat quitte la station sur cet objet.

### OnVideoEnd
`Event_OnVideoEnd`
Déclenché lorsque le lecteur vidéo sur cet objet a fini de jouer, soit à la fin de la vidéo soit par interaction du joueur.

### OnVideoError
`Event_OnVideoError`
Sorties : `videoError` - `VRC.SDK3.Components.Video.VideoError`
Déclenché lorsque le lecteur vidéo rencontre une erreur lors du chargement de la vidéo.

### OnVideoLoop
`Event_OnVideoLoop`
Si la lecture en boucle est activée, déclenché lorsque le lecteur vidéo termine une boucle.

### OnVideoPause
`Event_OnVideoPause`
Déclenché lorsque le lecteur vidéo sur cet objet est mis en pause.

### OnVideoPlay
`Event_OnVideoPlay`
Déclenché lorsque le lecteur vidéo sur cet objet démarre la lecture, soit par le début d'une nouvelle vidéo dans une file d'attente, la reprise de lecture ou par interaction du joueur.

### OnVideoStart
`Event_OnVideoStart`
Déclenché lorsque le lecteur vidéo sur cet objet démarre la lecture à partir d'un état arrêté.

### OnVideoReady
`Event_OnVideoReady`
Déclenché lorsque le lecteur vidéo a chargé une nouvelle vidéo.

# Événements du joueur
### OnPlayerTriggerEnter
`Event_OnPlayerTriggerEnter`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché lorsque la capsule d'un joueur entre dans un déclencheur collider.

### OnPlayerTriggerStay
`Event_OnPlayerTriggerStay`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché à chaque image lorsque la capsule d'un joueur est à l'intérieur d'un déclencheur collider.

### OnPlayerTriggerExit
`Event_OnPlayerTriggerExit`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché lorsque la capsule d'un joueur sort d'un déclencheur collider.

### OnPlayerCollisionEnter
`Event_OnPlayerCollisionEnter`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché lorsque la capsule d'un joueur entre en collision avec un collider.

### OnPlayerCollisionStay
`Event_OnPlayerCollisionStay`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché à chaque image lorsque la capsule d'un joueur est à l'intérieur d'un collider.

### OnPlayerCollisionExit
`Event_OnPlayerCollisionExit`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché lorsque la capsule d'un joueur sort d'un collider.

### OnPlayerParticleCollision
`Event_OnPlayerParticleCollision`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché lorsqu'une particule entre en collision avec la capsule d'un joueur, à condition que le système de particules ait l'option Collision et Envoyer des messages de collision activée.

### OnPlayerRespawn
`Event_OnPlayerRespawn`
Sorties : `player` - `VRC.SDKBase.VRCPlayerApi`
Déclenché lorsqu'un joueur réapparaît en utilisant son menu.

### Notes avancées
Tous les nœuds de cette liste sont de type `System.Void`.