

# Input

Dans ClientSim, tous les appels d'entrée sont regroupés dans une seule classe pour gérer les entrées et envoyer des événements. Le ClientSimInputManager utilise le nouveau système d'entrée, ce qui permet une gestion des entrées basée sur les événements. Il utilise le composant PlayerInput pour accéder aux événements d'entrée spécifiques en fonction des liaisons d'entrée affichées ci-dessous. Étant donné que le package du nouveau système d'entrée Unity n'est pas inclus par défaut et qu'Unity nécessite un paramètre spécial pour l'activer, toutes les références au système d'entrée sont enveloppées dans des conditions de définition, ce qui évite les erreurs lors de l'importation dans de nouveaux projets.

## Événements d'entrée

De manière similaire à [EventDispatcher](event-dispatcher.md), l'InputManager a également ses propres événements auxquels différents systèmes peuvent écouter directement. Ces événements sont séparés de l'EventDispatcher lui-même car tous les événements d'entrée ont des paramètres similaires et contiennent également des valeurs d'entrée qui ne sont pas diffusées via des événements mais nécessitent que le système d'écoute interroge les valeurs de l'axe mises à jour.

## Liaisons d'entrée

Le système d'entrée permet également différentes liaisons pour différents schémas de contrôle. Voir ci-dessous les liaisons incluses : KeyboardMouse, Gamepad et les liaisons expérimentales du contrôleur XR. Notez que les liaisons d'entrée XR dans InputSystem sont très limitées dans Unity 2019. L'InputManager devra être étendu pour prendre en charge correctement les différents contrôleurs VR.

## UdonInput

Le système UdonInput fait partie du prefab InputManager, qui s'abonne aux événements appropriés dans l'InputManager et interroge également les mises à jour des entrées de mouvement et de regard. En raison de la synchronisation entre le moment où Unity envoie les événements d'entrée et le moment où Udon doit recevoir les événements d'entrée, toutes les entrées basées sur des boutons sont mises en file d'attente et traitées ultérieurement dans la frame, en même temps que les entrées de mouvement et de regard. Cette mise en file d'attente et ce traitement permettent aux événements d'entrée de se produire après l'appel de la méthode de mise à jour d'Udon, de manière similaire à ce qui se passe dans VRChat.