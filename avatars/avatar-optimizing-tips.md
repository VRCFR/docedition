

:::caution

**Ce guide n'est pas destiné à être la référence absolue de l'optimisation des avatars !** Pour optimiser correctement votre avatar, il est nécessaire d'avoir de bonnes connaissances dans de nombreux domaines. Nous ne nous attendons pas à ce que tout le monde connaisse tout.

Cependant, nous faisons de notre mieux pour mettre à jour ce document avec les choses les plus couramment négligées et les cibles les plus importantes à atteindre.

Si vous avez des suggestions sur les conseils d'optimisation, veuillez utiliser le bouton **Suggérer des modifications** en haut à droite et ajouter vos propres conseils !
:::

Vous voulez que votre avatar soit efficace et aimé de tous grâce aux nombreuses images que vous économisez ? Suivez ces conseils et vous devriez être satisfait !

Tous les chiffres ou limites recommandés dans ce document peuvent changer à tout moment. Bien que certaines des descriptions fournies ci-dessous ne soient pas précises d'un point de vue technique, ce document est destiné à aider les utilisateurs novices à apprendre comment optimiser leurs avatars.

Des outils créés par la communauté comme [Cats Blender Plugin](https://github.com/michaeldegroot/cats-blender-plugin) (licence MIT) permettent aux utilisateurs d'optimiser très facilement leurs modèles et de résoudre les problèmes courants des avatars VRChat. Nous recommandons vivement l'utilisation de ces outils ! Cela rend votre travail plus facile et améliore les performances pour tous.

Au fait, le panneau de contrôle de construction du SDK fournit des informations sur le nombre de composants des avatars pour vous aider à les optimiser.

## N'utilisez pas Dynamic Bones !
Dynamic Bones est un asset Unity que vous pouvez acheter pour définir des os sur le squelette de votre avatar et les faire bouger comme s'ils étaient suspendus. Vous pouvez également définir des forces statiques comme la gravité, ce qui permet aux cheveux de tomber de manière plus réaliste.

Dynamic Bones est déconseillé et finira par être supprimé. Utilisez plutôt [PhysBones](/avatars/avatar-dynamics/physbones).

VRChat convertira automatiquement les Dynamic Bones en PhysBones lors de l'exécution.

## Limitez l'utilisation de cloth
Le cloth est un composant par défaut Unity qui a un coût similaire à celui des Dynamic Bones, mais qui est plus difficile à configurer. Limitez fortement son utilisation et ne l'appliquez pas aux meshes ayant plus d'environ 200 vertices environ.

## Réduisez le nombre de meshes sur votre avatar
Il existe deux types de Mesh Renderers possibles sur votre avatar : les Static Mesh Renderers et les Skinned Mesh Renderers. Les Static Meshes ne se déforment pas. Les Skinned Meshes, en revanche, ont généralement des rigs (os) qui indiquent au moteur comment déplacer et déformer le mesh en fonction de la position des os. Ces Skinned Meshes sont beaucoup plus coûteux, et vous ne devriez avoir qu'un seul Skinned Mesh Renderer sur votre avatar. Il y a très peu de raisons d'en avoir plus d'un - la plupart du temps, des éléments supplémentaires peuvent être intégrés au modèle d'origine.

De plus, chaque mesh supplémentaire sur votre avatar