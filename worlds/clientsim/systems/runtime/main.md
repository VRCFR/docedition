

# Client Sim Main

ClientSimMain est le point central de ClientSim qui gère l'initialisation et la destruction de ClientSim. Il est contenu dans le prefab ClientSimSystem. A sa création, tous les systèmes principaux seront initialisés avec leurs dépendances. Ce système maintient également toutes les implémentations des crochets VRCSDK pour lier les composants VRC aux Helpers de ClientSim. ClientSimMain est un singleton afin de garantir qu'une seule instance fonctionne à la fois et de faciliter le transfert d'informations depuis les fenêtres de l'éditeur et les tests. Aucun des systèmes en cours d'exécution dans ClientSim ne dépend du fait que ClientSimMain soit un singleton.

![Hiérarchie de ClientSimSystem](/images/client-sim-main-hierarchy.png)