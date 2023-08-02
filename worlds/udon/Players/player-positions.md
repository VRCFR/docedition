

Voici les nœuds relatifs aux positions des joueurs. Pour les nœuds qui traitent des forces liées aux joueurs, voir [Forces des joueurs](/worlds/udon/players/forces-des-joueurs).

### GetPosition

_retourne un Vector3 dans l'espace mondial_  
Obtient la position du joueur.

### GetRotation

_retourne une UnityEngine.Quaternion dans l'espace mondial_  
Obtient la rotation du joueur.

### GetBonePosition

_retourne un Vector3 dans l'espace mondial_  
Obtient la position de l'os spécifié dans l'avatar du joueur, ou Vector3.Zero (0,0,0) si l'os n'existe pas. Notez que les avatars peuvent ne pas avoir tous les mêmes os à des emplacements attendus, soyez donc prudent lorsque vous faites des suppositions sur des attributs tels que la taille du joueur, la pose, etc. en fonction de la position des os.

### GetBoneRotation

_retourne un Quaternion dans l'espace mondial_  
Obtient la rotation de l'os spécifié dans l'avatar du joueur, ou Quaternion.Identity (0,0,0,1) si l'os n'existe pas. Notez que les avatars peuvent ne pas avoir tous les mêmes os aux emplacements attendus, soyez donc prudent lorsque vous faites des suppositions sur des attributs tels que la taille du joueur, la pose, etc. en fonction de la rotation des os.

### GetTrackingData

_retourne des données de suivi pour le type de suivi spécifié : Head, LeftHand, RightHand ou Origin_  
Obtient une structure appelée TrackingData, qui contient des données de position et de rotation séparées. C'est la méthode recommandée pour obtenir des données de position et de rotation pour la tête et les mains d'un joueur. Cela renvoie des données provenant du TrackingManager pour un joueur local (c'est-à-dire les données provenant de leur casque / capteurs) et des os RightHand, LeftHand et Head pour un joueur distant. Origin renvoie le centre de l'espace de jeu VR local de l'utilisateur, tout en renvoyant la position du joueur pour les utilisateurs de bureau locaux et tous les utilisateurs distants.

### GetVelocity / SetVelocity

_retourne un Vector3 dans l'espace mondial_  
Obtient et définit la vitesse et la direction du mouvement du joueur. Si SetVelocity est appelé sur un joueur local, sa propriété 'IsGrounded' est définie sur false car il n'a pas le contrôle direct de ses mouvements pendant cette opération.

### IsPlayerGrounded

_retourne un booléen_  
Indique si le joueur touche le sol, ce qui lui permet de sauter.

### TeleportTo

_prend une position Vector3 dans l'espace mondial et une rotation Quaternion dans l'espace mondial_  
Envoie un joueur vers un nouvel endroit et une rotation spécifiée, à moins qu'une station ne l'interdise.