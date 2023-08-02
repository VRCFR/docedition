

Créer du contenu pour VRChat Quest est un défi - vous devez créer un contenu attrayant et captivant tout en optimisant le contenu pour les appareils mobiles. Ce sont les mêmes défis auxquels les développeurs de jeux doivent faire face lorsqu'ils construisent pour mobile.

Ici, nous vous donnerons quelques directives générales à garder à l'esprit lors de la création de contenu pour VRChat Quest.

Les éléments ci-dessous s'appliqueront aux avatars et aux mondes, sauf indication contraire.

Unity propose un guide pour [Optimiser vos expériences VR/AR](https://learn.unity.com/tutorial/optimizing-your-vr-ar-experiences) qui contient de nombreux points importants.

Il y a aussi cette [excellente vidéo sur l'optimisation de votre contenu VR par Lucas Rizzotto](https://www.youtube.com/watch?v=w0n4fuC4fNU) ! Elle est très bien faite et couvre beaucoup de ce que nous abordons ici. **Cette vidéo n'a pas été créée par VRChat ou pour VRChat spécifiquement, et attention, elle contient un langage fort.** Beaucoup des éléments de cet article sont abordés dans cette vidéo.

Enfin, tous les éléments de cette liste sont sujets à des changements. Autrement dit, nous n'avons pas encore finalisé les restrictions et les recommandations, alors gardez cela à l'esprit.

# Respect des limites
L'Oculus Quest a plusieurs limites strictes (et souples) pour le contenu des avatars. Consultez les [Limitations de contenu pour Quest](/platforms/android/quest-content-limitations) pour en savoir plus, ainsi que notre page sur le [Système de classement de performance des avatars](/avatars/avatar-performance-ranking-system) pour plus de détails sur le fonctionnement du blocage.

Si vous téléchargez un avatar ou un monde d'avatar qui dépasse largement nos recommandations, ce monde ou cet avatar peut être supprimé de l'accès public.

# Profiler Unity
Nous vous recommandons vivement d'utiliser le [Profiler Unity](https://docs.unity3d.com/Manual/Profiler.html). Avec le profiler, vous pouvez quantifier des valeurs précises pour différentes mesures de performance de votre monde ou de votre avatar. Il peut être particulièrement intéressant de mesurer le nombre d'appels de rendu dans une scène, ou la part proportionnelle du temps de frame qu'un composant utilise.

Bien sûr, le profiler sur votre puissant ordinateur ne reflétera pas exactement l'apparence d'un profiler sur Quest, mais vous pouvez quand même voir que le composant X utilise beaucoup plus de temps de frame que le rendu, ou autre, cela reste relatif !

Il existe de nombreux tutoriels sur l'utilisation du Profiler Unity, notamment deux proposés par Unity : [Présentation du Profiler pour débutants](https://unity3d.com/learn/tutorials/topics/interface-essentials/profiler-overview-beginners) et [Introduction intermédiaire au Profiler](https://unity3d.com/learn/tutorials/topics/interface-essentials/introduction-profiler). Ces tutoriels ont été réalisés pour des versions plus anciennes de Unity, mais ils couvrent encore assez bien les concepts de base.

# Taille du fichier
Vous disposez d'une quantité limitée de mémoire sur les plateformes mobiles, il est donc très important de le garder à l'esprit. Vous pouvez voir la taille de vos ressources une fois que vous avez construit le contenu (cliquez sur "Build & Publish" dans le SDK) et recherchez "statistics" dans votre logiciel d'édition. La taille pré-compressée est celle que vous recherchez.

En règle générale, évitez les textures volumineuses (>1ko). Elles sont les principales responsables d'une utilisation élevée de la mémoire. L'utilisation de couleurs de sommet et de couleurs plates peut grandement aider à réduire la taille des textures.

Veuillez noter que la compression Crunch ne réduit pas la taille en mémoire ! La compression Crunch ne réduit que la taille du téléchargement. Votre paquet de contenu doit respecter les limites sans Crunch.

### Mondes

Vous ne pouvez pas télécharger ou accéder à des mondes dont la taille dépasse 100Mo après compression à l'étape de construction pour VRChat Quest.

### Avatars

Vous devez viser un maximum de 5-8 Mo. Vous ne pouvez pas télécharger ou porter/visualiser des avatars dont la taille dépasse 10Mo après compression à l'étape de construction pour VRChat Quest.

# Nombre de polygones
Il est important de maintenir un faible nombre de polygones sur les plateformes mobiles. Bien que le Quest soit assez puissant pour un casque mobile, ses capacités matérielles ont des limites. Surveiller le nombre de polygones est très important pour maintenir de bonnes performances.

Ces recommandations sont techniquement appliquées via notre [Système de classement de performance des avatars](/avatars/avatar-performance-ranking-system).

### Mondes

Lors de la construction de mondes, essayez de maintenir un faible nombre de polygones. Vous devez également prévoir de la place pour les avatars des utilisateurs. **Nous vous recommandons de prévoir environ 50 000 triangles au total pour votre monde.**

### Avatars

Les mêmes règles générales s'appliquent aux avatars qu'aux mondes. Gardez à l'esprit que vous pouvez avoir 10 utilisateurs ou plus dans la même pièce, vous devrez donc prévoir une utilisation importante de triangles. **Nous vous recommandons d'essayer de rester en dessous de 10 000 triangles pour votre avatar.**

**Une limite stricte de polygones