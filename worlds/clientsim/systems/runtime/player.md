

# Joueur

La représentation ClientSim d'un joueur a été divisée en plusieurs composants par rapport à CyanEmu. Chaque composant gère un aspect différent du joueur. Ci-dessous, vous pouvez voir la hiérarchie des préfabriqués des joueurs locaux et distants.
![Hiérarchie du joueur local](/images/player-local-hierarchy.png)![Hiérarchie du joueur distant](/images/player-remote-hierarchy.png)

## ClientSimPlayer

La classe ClientSimPlayer est le conteneur qui détient tous les systèmes du joueur. Bien que les joueurs locaux et distants aient tous deux un ClientSimPlayer, il n'est initialisé que pour le joueur local. Tous les systèmes du joueur distant sont laissés vides, à l'exception des données changeables de [Avatar](#avatar) et VRCPlayerApi. Le ClientSimPlayer est le premier composant sur l'objet de niveau supérieur dans les préfabriqués des joueurs. Dans l'inspecteur, vous pouvez afficher et modifier les données VRCPlayerApi telles que les paramètres de locomotion et les paramètres audio en temps réel.

## TrackingProvider

L'interface TrackingProvider est une façon générique de définir comment les données de suivi du joueur doivent être contrôlées. La classe abstraite TrackingProviderBase fournit des données sur la position de la tête, des mains et de l'espace de jeu, et détermine également la posture actuelle du joueur en fonction de la hauteur de la tête. Le fournisseur de suivi peut être mis à l'échelle pour déplacer la caméra du joueur vers le haut ou vers le bas, ce qui permet de tester différents scénarios d'avatar de joueur. Il écoute les événements PlayerHeightUpdate et calcule une nouvelle échelle de suivi en fonction de la hauteur demandée du joueur. La hauteur par défaut de l'avatar est de 1.9, ce qui représente une échelle de suivi de 1. Étant donné que cette classe est abstraite, elle doit être étendue pour être utilisée dans ClientSim. Actuellement, seul le DesktopTrackingProvider est inclus dans ClientSim. Pour implémenter la réalité virtuelle dans ClientSim, il faudrait un nouveau VRTrackingProvider. Le fournisseur de suivi est censé être un enfant du [PlayerController](#playercontroller), mais devra être réétudié lors de l'implémentation de la réalité virtuelle, car le décalage x/z de l'espace de jeu n'est pas appliqué au joueur.

### DesktopTrackingProvider

Actuellement, le seul TrackingProvider implémenté pour ClientSim. Ce fournisseur de suivi bloque la position des mains par rapport à la caméra. La hauteur de la caméra est modifiée en fonction des [événements d'entrée Accroupir et s'allonger](input.md). À chaque image, ce fournisseur de suivi vérifie les modifications de l'entrée de vision et met à jour la rotation x de la caméra (haut/bas). Si le joueur est assis dans une station, alors la rotation y de la tête est débloquée pour permettre au joueur de regarder à gauche, à droite et jusqu'à 90 degrés en rotation de l'espace de jeu.

## PlayerController

Le PlayerController ne contrôle maintenant que le mouvement du joueur. Dans CyanEmu, la classe PlayerController contenait tout ce qui était lié au joueur. Ces systèmes ont maintenant été séparés, ce qui permet au PlayerController de se concentrer uniquement sur la gestion du mouvement du joueur. À chaque image, le contrôleur vérifiera l'entrée de mouvement ainsi que la posture du [TrackingProvider](#trackingprovider) pour savoir combien le joueur doit bouger à cette image.

## PlayerStationManager

Le PlayerStationManager gère la manière dont les joueurs interagissent avec les stations. Il stocke la station actuelle dans laquelle se trouve le joueur, ainsi que si le joueur est verrouillé sur la station. Lorsqu'il est verrouillé sur une station, à la fin de l'image, pour toutes les méthodes Update, LateUpdate et FixedUpdate, la position du [PlayerController](#playercontroller) est mise à jour sur celle de la station. Cela se produit à la fin de l'image pour s'assurer que tout autre script modifiant la position de la station se produit en premier.

## InteractManager

L'InteractManager est responsable de déterminer si un GameObject donné peut être interactif et d'effectuer l'interaction. Il calcule la distance actuelle à laquelle le joueur peut interagir à l'aide de [l'échelle de suivi](#trackingprovider) actuelle du TrackingProvider et de la valeur de proximité de chaque interaction.

## Raycaster

La détection des interactions de ClientSim est gérée par les Raycasters. Ce système recherchera des éléments interactifs en fonction d'un rayon fourni utilisé dans Physics.Raycast. Le [InteractiveLayerProvider](interactive-layer-provider.md) est utilisé pour savoir quelles couches prendre en compte lors des lancers de rayons. Tous les objets touchés sont ensuite filtrés en fonction des composants trouvés. Les objets avec UIShape sont toujours prioritaires en premier. L'InteractManager est utilisé pour déterminer les composants de l'objet pouvant être interactifs. Pour chaque lancer de rayon, un RaycastResult est renvoyé. Celui-ci contient des informations sur le rayon, l'objet touché et le type d'interaction, s'il y en a une.

### RayProvider
Le Raycaster utilise un RayProvider pour savoir dans quelle direction et à partir de quel point lancer le rayon. Les RayProviders sont une façon générique de fournir le rayon sans connaître les détails exacts. ClientSim implémente deux RayProviders :

#### CameraRayProvider
Étant donné une caméra et la position actuelle de la souris, crée un rayon qui passe par la souris depuis la caméra. C'est le RayProvider utilisé lorsque le TrackingProvider n'est pas en réalité virtuelle (mode bureau).

#### TransformRayProvider
Étant donné une transformation, crée un rayon basé sur la position de la transformation et la direction vers l'avant. Cela est utilisé pour lancer des rayons à partir des mains lorsque le TrackingProvider est en réalité virtuelle.

## PlayerRaycaster

Le PlayerRaycaster est responsable de la recherche des interactions dans le monde et de l'envoi d'événements en fonction de ce qu'il trouve. Il mettra également à jour le système [PlayerHand](#playerhand) pour les deux mains gauche et droite. Lorsqu'il est initialisé, le PlayerRaycaster créera deux [Raycasters](#raycaster), un pour la main gauche et un autre pour la main droite. Si le TrackingProvider n'est pas en réalité virtuelle (mode bureau), alors la main droite utilise un Raycaster avec un [RayProvider](#rayprovider) basé sur la souris. La main gauche n'est pas initialisée car elle ne sera jamais utilisée lorsque la réalité virtuelle n'est pas activée. Si le [TrackingProvider](#trackingprovider) est en réalité virtuelle, alors les Raycasters gauche et droite sont initialisés avec une source de rayons basée sur une transformation utilisant les transformations des mains du TrackingProvider. À chaque image, les deux systèmes Raycaster de la main sont mis à jour pour rechercher des éléments interactifs et les résultats sont envoyés via le [EventDispatcher](event-dispatcher.md). La dernière interaction trouvée est enregistrée pour chaque main en tant qu'interaction survolée. Si une interaction survolée est un objet Pickupable, cet objet Pickupable est défini comme Pickupable survolé pour la main donnée. Si l'action d'utilisation se produit pour une main donnée pendant que l'interaction est survolée, alors l'objet survolé sera interagi avec.

## PlayerHand

Le système PlayerHand est responsable de la gestion des objets Pickupable. Le [PlayerRaycaster](#playerraycaster) définira le pickup survolé actuel. Ensuite, le PlayerHand écoutera les événements d'entrée Grab pour savoir quand prendre le Pickupable survolé. PlayerHand écoutera également les événements d'utilisation et de largage pour effectuer des actions sur le Pickupable actuellement tenu. Si le pickup est cinématique, alors la position du pickup sera directement définie à chaque image pour correspondre à la transformation du rigidbody du PlayerHand. Si le pickup n'est pas cinématique, il sera attaché au rigidbody du PlayerHand à l'aide d'une articulation fixe. Lorsqu'il tient un pickup dans la main droite, le pickup peut être manipulé à l'aide des différentes liaisons Manipulate.

## PlayerAvatarManager

Le PlayerAvatarManager gère les éléments liés à l'avatar du joueur. Les joueurs locaux et distants ont tous deux un gestionnaire d'avatar. L'avatar pour tous les joueurs est le robot par défaut VRChat. Le gestionnaire est responsable de fournir des informations sur l'avatar à VRCPlayerApi. Les méthodes GetBonePosition et GetBoneRotation sont implémentées ici en tant qu'enveloppes autour d'Animator.GetBoneTransform. Le gestionnaire d'avatar du joueur local est le seul qui est correctement initialisé, ce qui lui permet d'écouter les [événements](event-dispatcher.md) de modification de l'échelle de suivi, qui mettent ensuite à jour l'échelle de l'avatar pour correspondre à la nouvelle échelle de suivi.

## Reticle

Le système ClientSimReticle est responsable de l'affichage d'une icône de réticule au centre de la fenêtre de jeu Unity. Ce système ne devrait être disponible que pour le [DesktopTrackingProvider](#desktoptrackingprovider). Le réticule peut être désactivé via le menu des paramètres. En plus du réticule central, chaque fois que le [PlayerRaycaster](#playerraycaster) survole un objet avec une forme UIShape, il affiche un pointeur sur la position de la souris. Ce pointeur n'est pas limité au centre de l'écran et sera toujours affiché même lorsque la souris est relâchée. La position de la souris est fournie par [ClientSimBaseInput](input.md).