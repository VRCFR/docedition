

Vous pouvez interagir avec les joueurs de votre monde grâce à l'API du joueur VRCPlayerApi. Chaque joueur possède un objet VRCPlayerApi, et votre monde déclenche les événements OnPlayerJoined / OnPlayerLeft sur tout UdonBehaviour qui y est associé lorsque qu'un joueur rejoint ou quitte le monde.

Cette page contient des informations sur l'utilisation de certains nœuds généraux. Étant donné qu'il y a tant de choses que vous pouvez faire avec l'objet VRCPlayerApi, nous avons regroupé certaines informations sur les pages suivantes :

* [Obtenir des joueurs](/worlds/udon/players/getting-players)
* [Positions des joueurs](/worlds/udon/players/player-positions)
* [Forces des joueurs](/worlds/udon/players/player-forces)
* [Collisions des joueurs](/worlds/udon/players/player-collisions)
* [Audio des joueurs](/worlds/udon/players/player-audio)
* [Événements des joueurs](/worlds/udon/graph/event-nodes#player-events)

## Nœuds généralement utiles

### IsValid
*VRCPlayerApi, Booléen*
Avant d'essayer de récupérer ou de définir quelque chose sur un joueur, vérifiez si IsValid renvoie true. Si un joueur a quitté depuis que vous avez enregistré une référence à lui, cette méthode renverra False. Pour une utilisation plus facile sur le graphique, recherchez la méthode générique "IsValid" qui fonctionne pour n'importe quel objet, car elle vous donne des flux séparés pour True et False.
![index-59fc2c8-player-isvalid.png](/img/worlds/index-59fc2c8-player-isvalid.png)

### EnablePickups
*VRCPlayerApi, Booléen*
Désactivez la capacité du joueur à ramasser et utiliser les objets VRCPickup dans le monde. Cette propriété est activée par défaut, vous n'avez donc besoin d'utiliser cette méthode que si vous souhaitez la désactiver.

### get displayName
*VRCPlayerApi*
Obtenez le nom affiché pour le joueur (peut être différent du nom d'utilisateur, qui est utilisé pour se connecter à VRChat et n'est pas exposé publiquement)

### Get isLocal
in: *VRCPlayerApi*
out: *Booléen*
Indique si le joueur donné est le joueur local.

### Get isMaster
in: *VRCPlayerApi*
out: *Booléen*
Indique si le joueur donné est le joueur *Maître*. Il s'agit du joueur qui a créé l'instance ou celui qui a hérité du statut de Maître lorsque le dernier Maître a quitté.

### GetPickupInHand
in: *VRCPlayerApi, Main (aucun, gauche, droite)*
out: *VRCPickup*
Obtient l'objet de ramassage que le joueur tient dans la main spécifiée. Ne fonctionne que pour le joueur local. Renvoie null s'il n'y a aucun objet VRCPickup trouvé.

### IsOwner
in: *VRCPlayerApi, GameObject*
out: *Booléen*
Indique si un joueur est le propriétaire d'un GameObject donné, important pour la synchronisation.

### IsUserInVR
in: *VRCPlayerApi*
out: *Booléen*
Indique si un joueur utilise un casque VR.

### PlayHapticEventInHand
*VRCPlayerApi, Main, float, float, float*
Fait vibrer les contrôleurs haptiques du joueur s'il en possède. Les valeurs flottantes doivent être comprises entre 0 et 1. *durée* est la durée de la vibration, *amplitude* est l'intensité de la vibration et *fréquence* est la vitesse de la vibration. La sensation peut varier considérablement entre les contrôleurs.

### UseAttachedStation
*VRCPlayerApi*
Fait en sorte que le joueur monte dans la station qui se trouve sur le même GameObject que ce UdonBehaviour.

### SimulationTime
*Float*
Le temps de simulation d'un joueur.

### UseLegacyLocomotion
*VRCPlayerApi*
**NON RECOMMANDÉ** - active la locomotion héritée pour ce joueur.

## Système de combat
Les nœuds suivants sont en cours de révision - ils ne fonctionnent pas et ne sont pas recommandés pour une utilisation. Nous évaluons leur utilité et ils doivent être ignorés pour le moment:
* CombatGetCurrentHitpoints
* CombatGetDestructible
* CombatSetCurrentHitpoints
* CombatSetDamageGraphic
* CombatSetMaxHitpoints
* CombatSetRespawn
* CombatSetup