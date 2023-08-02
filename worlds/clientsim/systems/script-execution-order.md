

# Ordre d'exécution du script

| Ordre d'exécution | Nom du système       | Description                                                                                                                                                                 |
|------------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| -Infinity        | UnityInputSystem     | Unity InputSystem se met à jour avant tous les MonoBehaviours. Les entrées des boutons de l'utilisateur sont envoyées à ClientSimInput et des événements sont déclenchés. |
| -3000            | TrackingProvider     | La saisie est vérifiée pour mettre à jour le TrackingProvider. Par exemple : la rotation de la tête de l'ordinateur de bureau.                                               |
| -3000            | PlayerController     | Mettre à jour la position du joueur avant les rayons.                                                                                                                       |
| -2000            | PlayerRaycaster      | Mettre à jour la position des PlayerHands avec les données de la main du TrackingProvider. Effectuer un raycast pour trouver des objets interactifs dans le monde. Cela doit se faire avant la mise à jour des EventSystems. |
| -1000            | Système d'événements Unity | Envoyer des événements de souris pour interagir avec l'interface utilisateur. L'ordre ne peut pas être modifié.                                                         |
| 0                | ClientSimBehaviours |                                                                                                                                                                             |
| 0                | UdonBehaviour        | Envoyer des événements de mise à jour aux programmes Udon.                                                                                                                  |
| 1                | UdonInput            | Cela doit se produire après UdonBehaviour.Update pour garantir l'ordre correct des événements.                                                                             |
| 10000            | ClientSimBaseInput   | Mettre à jour les ticks d'image actuels pour les événements de saisie. Cela est nécessaire uniquement pour garantir que les tests et le mode de lecture se comportent de la même manière en ce qui concerne le traitement de l'entrée. |
| 30000            | PlayerStationManager | Mettre à jour la position des joueurs sur une station le plus tard possible afin que tous les autres scripts aient eu le temps de s'évaluer en premier.                 |
| 30001            | TooltipManager       | Mettre à jour la position des visuels d'info-bulle après finalisation de la position du joueur.                                                                            |
| 31000            | PostLateUpdater      | Événement PostLateUpdate de VRChat envoyé aux UdonBehaviours.                                                                                                               |