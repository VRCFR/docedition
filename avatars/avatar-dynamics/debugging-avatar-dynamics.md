

Comme Avatar Dynamics est un système complexe, il est compréhensible de faire des erreurs lors de la construction de votre avatar. Pour aider à tester et déboguer les problèmes, nous avons fourni aux utilisateurs quelques outils pour faciliter le processus.

### Débogage en jeu
<iframe src='https://gfycat.com/ifr/LiveWhimsicalGuineafowl' frameborder='0' scrolling='no' allowfullscreen width='640' height='404'></iframe>

En utilisant le Menu d'action, vous pouvez maintenant utiliser l'option de superposition d'avatar pour afficher des représentations visuelles à la fois des [PhysBones](/avatars/avatar-dynamics/physbones) et des [Contacts](/avatars/avatar-dynamics/contacts) en direct dans le jeu. Cela est utile pour voir exactement ce qui se passe, ou si les objets ont été configurés correctement.

### Débogage dans l'éditeur
Les [PhysBones](/avatars/avatar-dynamics/physbones) et les [Contacts](/avatars/avatar-dynamics/contacts) fonctionnent dans l'éditeur de la même manière que dans le client. En entrant en mode Lecture, vous pouvez simuler ces systèmes et voir comment votre avatar réagira sans avoir besoin de charger votre avatar.

Tant qu'un contrôleur d'animation a été ajouté au composant Animator de votre avatar, les paramètres seront mis à jour comme ils le seraient dans le jeu. N'oubliez pas d'ajouter le contrôleur d'animation avant d'entrer en mode Lecture !

De plus, même si aucun contrôleur d'animation n'est configuré, vous pouvez toujours examiner chaque composant et voir les valeurs qu'ils donneraient pour chaque paramètre.