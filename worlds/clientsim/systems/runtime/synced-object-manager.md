

# SyncedObjectManager

Le SyncedObjectManager garde une trace de tous les objets synchronisés initialisés (IClientSimSyncable) dans la scène. Ces objets synchronisés sont mis dans deux listes : une liste pour tous les objets synchronisés, et une autre pour tous les objets synchronisés de position. Le SyncedObjectManager a actuellement seulement deux fonctions principales. La première est de vérifier tous les objets synchronisés de position pour vérifier qu'ils sont au-dessus de la hauteur de réapparition. S'ils tombent en dessous de la hauteur de réapparition, ils sont réapparus à leur position de départ ou détruits, selon les paramètres dans le [SceneManager](scene-manager.md). La deuxième fonction est de s'assurer que les objets ont les propriétaires corrects lorsque qu'un joueur quitte. Le gestionnaire écoute l'événement OnPlayerLeft [Event](event-dispatcher.md), parcourt tous les objets pour vérifier si ce joueur était le propriétaire, puis définit ces objets pour qu'ils soient possédés par le joueur principal à la place. Ce transfert de propriété se produit avant que les programmes Udon soient informés du départ du joueur.


VRC.SDK3.ClientSim.ClientSimSyncedObjectManager