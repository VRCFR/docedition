


# Player Manager
Le système PlayerManager est responsable des données VRCPlayerApi pendant l'exécution de ClientSim. Ce système gère la création et la destruction des joueurs, la gestion du joueur actuel, et l'envoi des événements associés tels que OnPlayerJoin, OnPlayerLeft et OnNewMaster. Le PlayerManager est similaire à celui de CyanEmu, mais cette fois-ci c'est une classe instanciée plutôt que statique. La plupart des crochets du SDK VRCPlayerApi sont liés à des fonctions statiques au sein de cette classe.