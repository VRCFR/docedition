

:::caution Nécessite des connaissances sur Unity

Ce document est rédigé en supposant que vous connaissez un peu les [animateurs Unity](https://docs.unity3d.com/2019.4/Documentation/Manual/class-AnimatorController.html).
:::

Lorsque vous sélectionnez un état spécifique dans la vue de l'animateur, vous pouvez ajouter des comportements d'état. Ce sont un peu comme des composants pour les états. Ils font différentes choses. Essayez de les ajouter et vous verrez ce qu'ils peuvent faire !

Tous les comportements d'état s'exécutent à la première image de la transition vers cet état.

Les comportements d'état *devraient* s'exécuter quel que soit le temps passé dans la machine à états avec le comportement d'état.

:::caution

Le terme "devrait" est utilisé délibérément ici, car dans la [documentation Unity](https://docs.unity3d.com/2019.4/Documentation/Manual/StateMachineBehaviours.html), aucune garantie n'est donnée que les comportements d'état s'exécuteront avec de très petites durées de transition ou d'état.

Si vous voulez être **complètement** sûr, assurez-vous que le temps total passé dans l'état contenant le comportement d'état et toutes les transitions directes vers cet état est d'au moins 0,02 seconde - bien qu'en pratique, cela ne semble pas nécessaire.

:::

## Contrôleur de couche de l'animateur

![Unity_2020-07-08_12-50-04.png](/img/avatars/state-behaviors-e78eb77-Unity_2020-07-08_12-50-04.png)

Le contrôleur de couche de l'animateur vous permet de mélanger le poids d'une couche d'animateur spécifique à l'intérieur de n'importe quelle couche lisible pendant une période de temps donnée.

Si l'état est quitté pendant la durée de mélange, la couche cible est immédiatement réglée sur le poids cible.

Le poids de la couche restera jusqu'à ce qu'un autre état exécute à nouveau ce comportement d'état et le réinitialise.

Voici les informations reformatées dans un tableau Markdown à deux colonnes :

| Nom de la propriété | But |
| -------------- | -------------------------------------------------------------------------------------------- |
| Lisible       | Vous permet de sélectionner la couche lisible que vous affectez.                                  |
| Couche          | L'indice de la couche lisible que vous souhaitez affecter. Vous ne pouvez pas changer le poids de la 0ème couche de base, elle est toujours réglée sur un poids de 1,0. |
| Poids cible    | Définit le poids que vous souhaitez mélanger.                                                      |
| Durée du mélange | Définit la période de temps (en secondes) que vous souhaitez pour le mélange. 0 signifie instantané.        |
| Chaîne de débogage   | Lorsque ce comportement d'état s'exécute, cette chaîne sera imprimée dans le journal de sortie. Utile pour le débogage. |


## Contrôle de la locomotion de l'animateur

![state-behaviors-f6f3250-Unity_2020-07-08_13-16-13.png](/img/avatars/state-behaviors-f6f3250-Unity_2020-07-08_13-16-13.png)

Le contrôle de la locomotion de l'animateur vous permet de désactiver la locomotion dans un état donné d'un animateur. L'état de locomotion restera jusqu'à ce qu'un autre état exécute à nouveau ce comportement d'état et le modifie.

En mode bureau, cela désactive le mouvement de translation et restreint le mouvement de rotation (vue) à l'axe vertical. En réalité virtuelle, cela désactive le mouvement de translation et de rotation du contrôleur, et restreint la moitié du corps IK (le corps entier n'est pas affecté). Dans les deux modes, la capsule du joueur est figée en place.

| Paramètre | Description |
| :-- | :-- |
| Désactiver la locomotion | Si activé, la locomotion (déplacement avec les commandes) sera désactivée. Le déplacement dans l'espace de la pièce sera toujours possible. Si désactivé, la locomotion sera activée. |
| Chaîne de débogage | Lorsque ce comportement d'état s'exécute, cette chaîne sera imprimée dans le journal de sortie. Utile pour le débogage. |

## Espace de pose temporaire de l'animateur

![state-behaviors-467daaf-Unity_2020-07-14_21-38-14.png](/img/avatars/state-behaviors-467daaf-Unity_2020-07-14_21-38-14.png)

Le contrôle de l'espace de pose temporaire de l'animateur vous permet de déplacer le point de vue de la personne portant l'avatar vers la tête à ce moment précis