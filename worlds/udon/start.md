

## Qu'est-ce que Udon ?
**VRChat Udon** est un langage de programmation intégralement développé par l'équipe de développement de VRChat. Il a été conçu pour être sécurisé, performant et facile à utiliser grâce au **Graphique Udon Node de VRChat**, une interface de programmation visuelle intégrée qui utilise des nœuds et des connexions (que nous appelons "nouilles") pour relier les flux, les entrées et les sorties. Vous pouvez créer des comportements complexes avec Udon, bien plus complexes et faciles à comprendre que des chaînes de déclencheurs et d'actions difficilement manipulables.

Non seulement vous pouvez reproduire le comportement complet des déclencheurs et des actions avec VRChat Udon, mais vous pouvez également créer vos propres comportements, synchroniser des variables avec d'autres utilisateurs, interagir avec des scènes, interagir avec des joueurs, etc.

De plus, Udon fonctionne à la fois dans le client VRChat *et* dans l'éditeur Unity, ce qui vous permet de tester et de déboguer vos créations facilement.

Pour les personnes plus techniques : **VRChat Udon** est une machine virtuelle exécutant un bytecode compilé à partir d'**Udon Assembly**. Vous pouvez générer de l'**Udon Assembly** à l'aide de l'interface utilisateur intégrée au **Graphique Udon Node de VRChat**, en écrivant votre propre **Udon Assembly** ou même en écrivant votre propre compilateur pour générer directement de l'**Udon Assembly** ou des programmes en bytecode.

## État actuel d'Udon
**Udon est actuellement notre système standard principal pour la création de mondes !**

Vous pouvez utiliser le [Graphique Udon Node](/worlds/udon/graph) pour créer des programmes Udon avec une interface graphique. Cela ressemble beaucoup aux animateurs Unity, aux shaders ou aux nœuds de géométrie de Blender, aux blueprints Unreal, et à de nombreuses autres méthodes similaires. C'est un excellent point de départ, mais certaines personnes préfèrent simplement les nœuds au code !

Bien sûr, si vous préférez le code, vous pouvez toujours écrire de l'Udon à l'aide d'[UdonSharp](https://udonsharp.docs.vrchat.com/). UdonSharp vous permet d'écrire de l'Udon de manière très similaire à C#. Si vous êtes déjà familiarisé avec la programmation, U# pourrait être la méthode la plus simple pour vous.

## Comment utiliser Udon
Consultez le guide [Getting Started with Udon](/worlds/udon/getting-started-with-udon) !

Si vous préférez les didacticiels vidéo, vous pouvez consulter notre playlist [Learning Udon](https://www.youtube.com/playlist?list=PLe9XHNvXcouQjg5GULWGLj1tMzeythnQi) sur YouTube, qui explique toutes les étapes pour vous lancer.
<iframe class="embedly-embed" src="//cdn.embedly.com/widgets/media.html?src=http%3A%2F%2Fwww.youtube.com%2Fembed%2Fvideoseries%3Flist%3DPLe9XHNvXcouQjg5GULWGLj1tMzeythnQi&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fplaylist%3Flist%3DPLe9XHNvXcouQjg5GULWGLj1tMzeythnQi&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F8gXzBTqlP6I%2Fhqdefault.jpg%3Fsqp%3D-oaymwEWCKgBEF5IWvKriqkDCQgBFQAAiEIYAQ%3D%3D%26rs%3DAOn4CLDEoE6be2bvFU9le9GXGstXJO0nfg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube" width="853" height="480" scrolling="no" title="YouTube embed" frameborder="0" allow="autoplay; fullscreen" allowfullscreen="true"></iframe>
Si vous préférez lire directement les étapes, consultez notre page [Getting Started with Udon](/worlds/udon/getting-started-with-udon).

## Rapports de bugs et demandes de fonctionnalités
Nous utilisons Canny dans l'ensemble de VRChat pour recevoir les rapports de bugs et les demandes de fonctionnalités. Pour Udon en particulier, utilisez ces liens :
* [Bugs](https://feedback.vrchat.com/vrchat-udon-closed-alpha-bugs)
* [Demandes de fonctionnalités](https://feedback.vrchat.com/vrchat-udon-closed-alpha-feedback)