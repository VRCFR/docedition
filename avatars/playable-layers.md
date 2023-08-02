

Lorsque vous créez des animations pour votre avatar VRChat, vous utiliserez les "couches jouables" de VRChat. Elles permettent de séparer proprement certaines actions que vous souhaitez effectuer avec votre avatar dans leurs propres animations, telles que courir, sauter, donner un pouce levé, sourire, remuer la queue, ou des combinaisons de celles-ci.
:::caution Connaissance de Unity requise

Ce document est rédigé en supposant que vous connaissez un peu les [animateurs Unity](https://docs.unity3d.com/2019.4/Documentation/Manual/class-AnimatorController.html).
:::

Dans le descripteur d'avatar Avatars 3.0, il y a cinq boutons étiquetés :
- Base
- Additive
- Gesture (Geste)
- Action
- FX

Ce sont les **couches jouables**. Chacune d'entre elles utilise un "animateur Unity" et elles se superposent les unes aux autres. En d'autres termes, vous disposez de cinq "animateurs racine" avec lesquels vous pouvez jouer, et chacun d'entre eux peut avoir plusieurs **couches d'animations**.

Ces couches s'appliquent dans l'ordre : Base est appliquée en premier, puis Additive, puis Gesture, Action, et enfin FX. Par exemple, si quelque chose dans "Additive" anime un os (avec un poids de 1,0), et ensuite quelque chose dans "Action" anime ce même os (avec un poids de 1,0), l'animation de "Action" aura la priorité.

Nous avons des exemples de couches jouables disponibles dans le SDK. Selon votre manière d'apprendre et de travailler avec, il pourrait être plus facile pour vous d'utiliser et de modifier ces couches par défaut pour comprendre comment cela fonctionne !

Lorsque vous utilisez VRChat avec un avatar Avatar 3.0, toutes ces couches jouables sont regroupées dans un "animateur combiné". Cet "animateur" est l'animateur principal de votre avatar, et vous pouvez contrôler n'importe quelle partie de celui-ci. **Cela signifie qu'il n'est pas nécessaire d'ajouter d'autres animateurs à votre avatar.**

En parenthèse, vous ne devriez jamais utiliser le même contrôleur dans plusieurs couches jouables. Cela peut fonctionner pour certains paramétrages, mais c'est une pratique **très** mauvaise et cela posera de gros problèmes à mesure que vous étendez la fonctionnalité de votre avatar.
:::danger Utiliser uniquement des contrôleurs d'animation

Nous ne supportons que l'utilisation des contrôleurs d'animation dans les emplacements des couches jouables. N'utilisez aucun autre type de contrôleur, vous risquez d'obtenir des erreurs ou de ne pas pouvoir charger le contenu.
:::

Que font ces couches jouables ? Voici une version raccourcie :

**Base :** Ce qui doit toujours être joué, réagir au mouvement (comme la locomotion), ou à l'état de locomotion de votre avatar (course, chute, accroupissement, etc). Les animations de transformation seulement.
**Additive :** Ce qui est déjà utilisé dans "Base", mais que vous voulez "ajouter" - comme une animation de respiration. Les animations de transformation seulement.
**Gesture (Geste) :** Les choses déclenchées par la main OU par le menu d'expression. Vous pouvez également l'utiliser pour les "animations d'attente", comme une queue qui remue, des ailes qui battent ou des oreilles qui bougent. Les animations de transformation seulement.
**Action :** Remplace entièrement les autres couches, similaire aux "emotes" AV2. Les animations de transformation seulement.
**FX :** Comme les gestes, mais pour tout ce qui n'est pas une position de transformation, une rotation ou une animation d'échelle.

C'est génial, mais rentrons un peu plus dans les détails.

## Base

La couche "Base" contient les animations de locomotion, y compris les arbres de transition pour la marche, la course, et l'écartement. Elle comprend également les états d'animation pour le saut, la chute, la chute rapide, l'accroupissement, le rampement, entre autres choses.

Gardez à l'esprit que si vous ajoutez quelque chose ici, vous devrez redéfinir les états de vos animations de locomotion. C'est assez complexe ! Jetez un œil à l'exemple de la couche "Base" pour voir à quel point cela peut être complexe.

Les animations dans "Base" ne doivent affecter que les transformations, et toutes les couches doivent utiliser des masques d'avatar pour vous assurer de n'affecter que les transformations appropriées.

## Additive

La couche "Additive" est destinée aux mouvements de transformation supplémentaires par-dessus les os humanoïdes animés dans "Base" - comme des animations de respiration qui peuvent être ajoutées à la couche "Base".

**Si vous voulez ajouter une animation d'attente sur des os non-humanoides - comme une queue, des oreilles, etc. - utilisez Gesture à la place !** "Additive" est *spécifiquement* pour les os humanoides.

La couche "Additive" est spéciale car elle est toujours configurée en mode de mélange "Additive". En bref, si vous avez une transformation qui bouge pendant la locomotion, l'animation "Additive" ajoutera son animation par-dessus. Cela peut avoir des comportements étranges si vous faites des choses compliquées avec les os dans "Additive", essayez donc de rester assez minimaliste.

:::caution Le premier masque de la couche "Additive" est ignoré

Le masque du premier niveau (première couche, 0e couche, etc.) est ignoré. C'est pour des raisons de masquage interne. Vous pouvez toujours masquer les autres couches, mais tout masque appliqué à la première couche sera ignoré.
:::

Les animations dans "Additive" ne doivent affecter que les transformations.

## Gesture (Geste)

La couche "Gesture"