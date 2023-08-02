


# Aides VRCSDK

Les composants Helper sont ajoutés à un objet pour aider à gérer le comportement des composants VRC SDK. Le rôle de ces composants reste le même par rapport à CyanEmu et à la phase 2, bien que certaines logiques qui ne sont pas spécifiques à la fonction de l'objet lui-même aient été supprimées. Par exemple, dans CyanEmu, le script CyanEmuPickupHelper gérait la logique pour tenir les objets à ramasser. Maintenant, ce comportement a été déplacé en dehors de la classe d'aide à la ramassage, et dans le système de gestion des ramassages. Le code du PickupHelper ne fournit désormais que des données sur la façon dont PlayerHand doit gérer le ramassage.

Les classes Helper peuvent également étendre des interfaces utilisées dans ClientSim. Il existe deux catégories d'interfaces : [Usables](#interfaces-utilisables) et [Handlers](#interfaces-de-gestion).

## Interfaces utilisables

Les interfaces utilisables se terminent généralement par "able" et représentent des objets qui peuvent être utilisés d'une certaine manière dans ClientSim. Elles fournissent des informations sur la façon dont elles peuvent être utilisées, mais n'incluent pas les méthodes pour les utiliser.

| Nom                       | Description                                                      |
|----------------------------|------------------------------------------------------------------|
| IClientSimInteractable     | Représente un objet avec lequel il est possible d'interagir       |
| IClientSimPickupable       | Représente un objet qui peut être ramassé, étend Interactable     |
| IClientSimStation          | Représente un objet que le joueur peut utiliser pour s'asseoir    |
| IClientSimSyncable         | Représente un objet qui peut avoir un propriétaire                |
| IClientSimPositionSyncable | Représente un objet qui synchronise sa position, étend Syncable   |

## Interfaces de gestion

En utilisant ces deux types d'interface, les classes Helper permettent d'encapsuler les informations des composants VRChat SDK pour les fournir à ClientSim.

| Nom                       | Description                                                      |
|----------------------------|------------------------------------------------------------------|
| PositionSyncedHelperBase   | Helper pour VRCObjectSync, étend PositionSyncedHelperBase. Syncable, PositionSyncable, RespawnHandler |
| ObjectSyncHelper           | Helper pour VRCObjectSync, étend PositionSyncedHelperBase. Syncable, PositionSyncable, RespawnHandler |
| UdonHelper                 | Helper pour UdonBehaviour, étend PositionSyncedHelperBase. Syncable, PositionSyncable, RespawnHandler, Interactable, PickupHandler, StationHandler, SyncableHandler |
| PickupHelper               | Helper pour VRCPickup. Pickupable                                 |
| StationHelper              | Helper pour VRCStation. Implémente IClientSimStation              |
| ObjectPoolHelper           | Helper pour VRCObjectPool. Syncable                               |
| CombatSystemHelper         | Helper pour Udon CombatSetup. Implémente IVRC_Destructible. Le composant Helper est ajouté directement à l'objet joueur lors de son initialisation. |
| SpatialAudioHelper         | Helper pour VRCSpatialAudioSource                                |