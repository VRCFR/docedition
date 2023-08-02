

:::caution Nécessite une connaissance de Unity
Ce document suppose que vous avez des connaissances de base sur [Unity Animators](https://docs.unity3d.com/2019.4/Documentation/Manual/class-AnimatorController.html).
:::

## Création d'un menu d'expressions

1. Cliquez avec le bouton droit de la souris dans le projet Unity, sélectionnez `Create/VRC Scriptable Objects/Expressions Menu`
2. Sélectionnez le nouvel objet dans le projet

Vous devrez également créer un objet ExpressionParameters, où vous pourrez définir tous les paramètres personnalisés que vous utilisez. Vous pouvez les nommer ici, ainsi que définir leur type. Vous créez un objet de la même manière que ci-dessus :

3. Cliquez avec le bouton droit de la souris dans le projet Unity, sélectionnez `Create/VRC Scriptable Objects/Expression Parameters`
4. Sélectionnez le nouvel objet dans le projet.
5. Configurez vos paramètres personnalisés avec des noms et des types. `Int` a une plage de 0 à 255, Float a une plage de -1.0 à 1.0. Vous pouvez accéder à vos paramètres avec vos noms personnalisés pour faciliter l'organisation.

Après cela, vous devrez revenir à votre menu d'expressions.

6. Dans l'inspecteur, cliquez sur "Add Control". Jusqu'à 8 contrôles peuvent être ajoutés à un menu.
7. Vous pouvez également nommer des états, ajouter des icônes et changer l'ordre des contrôles ici.
8. Lorsque vous avez terminé, faites glisser cet objet dans la propriété "Expressions Menu" de l'Avatar Descriptor.
9. Faites glisser votre objet Expressions Parameters dans la propriété "Expressions Parameters" de l'Avatar Descriptor.

FYI: nous avons inclus quelques icônes par défaut que vous pouvez utiliser dans `VRCSDK/Assets3/Expression Menu Icons/`.

### Types de contrôles

* **Bouton** - Définit un paramètre lorsqu'il est cliqué, puis le réinitialise après l'envoi de la synchronisation/réinitialisation - généralement après environ une seconde. Ne peut pas être maintenu enfoncé.
* **Toggle** - Définit un paramètre lorsque le toggle est activé, le réinitialise lorsque le toggle est désactivé.
* **Sous-menu** - Ouvre un autre menu d'expressions. De plus, il peut également définir un paramètre lors de l'entrée, si tel est le cas, ce paramètre est réinitialisé à zéro lorsque vous quittez ce menu.
  * **Note importante :** Vous pouvez mettre des sous-menus dans des sous-menus !

* **Two Axis Puppet** - Ouvre un menu de marionnettes à axe qui contrôle deux paramètres à virgule flottante en fonction de la position du joystick. Les paramètres sont attribués à la verticale et à l'horizontale. Les valeurs flottantes vont de -1.0 à 1.0.
* **Four Axis Puppet** - Ouvre un menu de marionnettes à axe qui contrôle quatre paramètres à virgule flottante en fonction de la position du joystick. Les paramètres sont attribués dans l'ordre, vers le haut, vers la droite, vers le bas, vers la gauche. Les valeurs flottantes sont de 0.0 à 1.0.
* **Radial Puppet** - Ouvre un menu de marionnettes radiales qui contrôle un seul paramètre à virgule flottante, un peu comme une barre de progression que vous pouvez remplir ! La valeur flottante est de 0.0 à 1.0.
:::note

Les **contrôles de marionnettes** utilisent la [**synchronisation IK**](/avatars/animator-parameters#sync-types) lorsqu'ils sont ouverts. Si vous souhaitez une synchronisation aussi proche que possible de vos entrées pour des mouvements rapides, vous devez utiliser un menu de marionnettes.\n\n**Bouton**/**Toggle** utilise la **synchronisation lisible** qui se met à jour à la demande, au lieu de manière continue, et convient aux choses que vous "allumez/éteignez" mais dont vous n'avez pas besoin d'une synchronisation très précise.\n\nLa synchronisation du menu de marionnettes se met toujours à jour à la fréquence maximale disponible, et elle lisse les valeurs pour les utilisateurs à distance - bien mieux lorsque la réplication temporelle est importante.",
  "title": "Synchronisation du menu de marionnettes"
:::
Les contrôles de marionnettes peuvent également définir un paramètre lors de l'entrée dans le menu.

Si vous utilisez le bouton de la manette pour quitter, alors les paramètres manipulés resteront à leur valeur jusqu'à ce que vous les changiez à nouveau - soit en réentrant dans un menu de marionnettes qui utilise ces paramètres, soit en les utilisant ailleurs.