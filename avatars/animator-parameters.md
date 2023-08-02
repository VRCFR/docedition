

:::caution[Connaissance de Unity requise]

Ce document part du principe que vous avez des connaissances de base sur les [animateurs Unity](https://docs.unity3d.com/2019.4/Documentation/Manual/class-AnimatorController.html).

:::

Voici une liste des paramètres (**sensibles à la casse**) pouvant être ajoutés à n'importe quelle couche de lecture (contrôleur d'animation) et pouvant être modifiés dans toutes les couches de lecture qui incluent ce paramètre. Les paramètres créés par l'utilisateur qui ne figurent pas dans cette liste ne seront présents que localement dans ce contrôleur d'animation et ne sont pas modifiables par l'avatar.

Vous devrez ajouter ceux-ci à vos animateurs de couche de lecture pour les utiliser. **Ils sont sensibles à la casse !**

> ❗️ Ne pas créer d'impasse !
> 
> Vous devez considérer que les valeurs des paramètres peuvent changer. Si vous créez une impasse dans vos animateurs, c'est-à-dire si vous n'avez pas de "sortie" dans une branche particulière, vous risquez d'avoir un avatar défectueux.

## Paramètres

| Nom                                                                        | Description                                                                                                                                                                        | Type        | Synchronisation |
| --------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | --------------- |
| IsLocal                                                                     | Vrai si l'avatar est porté localement, faux sinon                                                                                                                                  | Bool        | Aucune          |
| [Viseme](/fr/avatars/animator-parameters#les-valeurs-de-viseme)                 | [Indice de visème Oculus](https://developer.oculus.com/documentation/unity/audio-ovrlipsync-viseme-reference) (`0-14`). Lors de l'utilisation de Jawbone/Jawflap, la plage est de `0-100`, indiquant le volume                                          | Int         | Discours        |
| Voice                                                                       | Volume du microphone (`0.0-1.0`)                                                                                                                                                   | Float       | Discours        |
| [GestureLeft](/fr/avatars/animator-parameters#les-valeurs-de-gestureleft-et-gestureright)  | Gestuelle provenant du contrôleur de la main gauche (0-7)                                                                                                                         | Int         | IK              |
| [GestureRight](/fr/avatars/animator-parameters#les-valeurs-de-gestureleft-et-gestureright) | Gestuelle provenant du contrôleur de la main droite (0-7)                                                                                                                         | Int         | IK              |
| GestureLeftWeight                                                           | Déclencheur analogique L (0.0-1.0)†                                                                                                                                                | Float       | Lisible         |
| GestureRightWeight                                                          | Déclencheur analogique R (0.0-1.0)†                                                                                                                                                | Float       | Lisible         |
| AngularY                                                                    | Vélocité angulaire sur l'axe Y                                                                                                                                                    | Float       | IK              |
| VelocityX                                                                   | Vitesse de mouvement latéral en m/s                                                                                                                                               | Float       | IK              |
| VelocityY                                                                   | Vitesse de mouvement vertical en m/s                                                                                                                                              | Float       | IK              |
| VelocityZ                                                                   | Vitesse de déplacement avant en m/s                                                                                                                                                | Float       | IK              |
| VelocityMagnitude                                                           | Magnitude totale de la vitesse                                                                                                                                                     | Float       | IK              |
| Upright                                                                     | Indique si vous êtes "debout". 0 signifie "couché", 1 signifie "debout"                                                                                                             | Float       | IK              |
| Grounded                                                                    | Vrai si le joueur touche le sol                                                                                                                                                    | Bool        | IK              |
| Seated                                                                      | Vrai si le joueur est assis                                                                                                                                                        | Bool        | IK              |
| AFK                                                                         | Indique si le joueur est indisponible (capteur de proximité du