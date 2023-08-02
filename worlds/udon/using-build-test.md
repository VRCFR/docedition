
:::note Prérequis

Avant de lire cette page, vous devez lire [Qu'est-ce que Udon](/worlds/udon) et [Commencer avec Udon](/worlds/udon/getting-started-with-udon).
:::

<iframe class="embedly-embed" src="//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2Fvideoseries%3Flist%3DPLe9XHNvXcouQjg5GULWGLj1tMzeythnQi%26start%3D0&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3D8yaQY0arCnc&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2F8yaQY0arCnc%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube" width="854" height="480" scrolling="no" title="Embed YouTube" frameborder="0" allow="autoplay; fullscreen" allowfullscreen="true"></iframe>
Certaines fonctionnalités simples de votre monde fonctionneront simplement en appuyant sur 'Jouer' dans l'Éditeur - événements de souris, minuteries, choses qui ne nécessitent pas d'interaction des avatars ou de mise en réseau. Pour beaucoup des fonctionnalités intéressantes, vous devrez créer une version de votre monde qui s'exécute dans le client VRChat réel.

# Ouvrez la scène UdonExample

Ouvrez la scène UdonExample à partir du dossier Exemples de VRChat - cette scène contient de nombreux graphiques réutilisables à partir desquels vous pouvez apprendre. Tout est configuré pour fonctionner tel quel, nous pouvons donc l'utiliser pour nous assurer que tout fonctionne correctement.

# Configuration de vos paramètres

1. Commencez par créer un nouveau projet, en vous assurant que le SDK Worlds a été importé correctement, et en ouvrant le panneau de contrôle VRChat depuis la barre de menus sous VRChat SDK > Afficher le panneau de contrôle.
![](/img/worlds/using-build-test-e47cc0f-show-control-panel.png)

2. Entrez vos informations de connexion dans l'onglet 'Authentification' et appuyez sur 'Se connecter'.
![](/img/worlds/using-build-test-8c5c7ff-sign-in.png)

3. Cliquez sur l'onglet Paramètres et recherchez l'entrée 'Client VRChat' en bas. C'est le client VRChat que Unity utilisera pour tester vos mondes. Si vous ne définissez pas cela, vos mondes risquent de ne pas se lancer correctement.
![](/img/worlds/using-build-test-69f8274-installed-client-path.png)

Appuyez sur 'Modifier' pour afficher un explorateur de fichiers, puis naviguez jusqu'à l'endroit où vous avez installé VRChat et choisissez le programme VRChat.exe. Voici quelques emplacements par défaut où il pourrait se trouver :
* Steam : C:\Program Files (x86)\Steam\steamapps\common\VRChat\VRChat.exe
* Oculus : C:\Program Files\Oculus\Software\Software\vrchat-vrchat\VRChat.exe
* Viveport : C:\Viveport\ViveApps\469fbcbb-bfde-40b5-a7d4-381249d387cd\1597468388\VRChat.exe

4. Passez à l'onglet 'Constructeur'. Nous devons configurer nos couches et notre matrice de collision de la manière attendue par VRChat. Appuyez simplement sur le bouton 'Configurer les calques pour VRChat', puis sur 'Faire'. qui apparaît.
![](/img/worlds/using-build-test-5f05f9b-setup-layers.png)

Ensuite, faites de même pour le bouton 'Configurer la matrice de collision'.
![](/img/worlds/using-build-test-7ccc247-set-collision-matrix.png)

# Exécution de votre premier test

Avec tous nos paramètres corrects, nous sommes prêts à créer une version de la scène. Une fois que vous avez résolu les problèmes de l'onglet Constructeur en suivant les instructions ci-dessus, vous avez accès au bouton 'Build & Test'. Pour ce premier test, activez 'Force Non-VR', puis appuyez sur Construire & Test.
![](/img/worlds/using-build-test-8712faf-build-and-test.png)

Votre client VRChat devrait se lancer dans une copie locale de ce monde où vous pouvez vous déplacer et tout essayer !
![](/img/worlds/using-build-test-2acac91-UdonExampleScene.jpg)

# Lancement de plusieurs clients
Pour tester les variables synchronisées et les événements de réseau personnalisés, vous avez besoin de plusieurs personnes dans le même monde. Le moyen le plus simple d'y parvenir est d'utiliser l'onglet Constructeur pour lancer plusieurs clients. Fermez la fenêtre du client VRChat que vous venez de lancer s'il est toujours ouvert, et modifiez le 'Nombre de clients' pour le mettre à 2, puis appuyez encore une fois sur Construire et tester. Cette fois-ci, Unity ouvrira deux clients VRChat, avec le même avatar dans les deux. Vous pouvez passer d'une fenêtre à l'autre pour contrôler vos deux avatars, et même vous voir parler dans les deux. Essayez de jouer avec la zone des variables synchronisées. Le premier avatar qui se charge sera le Maître de l'instance et donc le Propriétaire de ces GameObjects, il pourra donc mettre à jour les éléments de l'interface utilisateur, tandis que le deuxième avatar ne pourra voir que les mises à jour. La seule exception dans cette scène est le 'SyncButtonAnyone' qui transfère la propriété à celui qui clique dessus.
:::danger Bug : N'utilisez pas la chaise lors de l'exécution de Build & Test avec plusieurs clients.

Il y a actuellement un problème selon lequel tous vos avatars s'asseyent sur la chaise, et il est difficile de les en sortir. Nous supprimerons cet avertissement lorsque le problème sera résolu. Pour l'instant, vous devrez publier la scène pour tester les stations dans votre monde.
:::
# Build & Reload
Lorsque vous testez de nombreux clients, il peut être fastidieux d'organiser vos fenêtres et d'attendre que VRChat se connecte à chaque fois que vous apportez une modification à votre monde. Vous pouvez modifier le 'Nombre de clients' pour le lancer à 0 et transformer "Build & Test" en "Build & Reload".
![Build & Reload!](/img/worlds/using-build-test-07685ac-build-and-reload.png)
Cela créera une nouvelle version de votre monde et déplacera tous les clients ouverts dans cette nouvelle instance locale, en sautant complètement la séquence de démarrage de VRChat.

Vous pouvez également le faire pour les clients que vous lancez vous-même, si vous souhaitez tester avec plusieurs profils. Vous pouvez utiliser le nouveau drapeau en ligne de commande `--watch-worlds` pour activer cette fonctionnalité. Par exemple, cette commande lance VRChat avec mon profil principal en mode bureau, avec un débogage complet, en 1920x1080, avec le rechargement des mondes activé.
```shell
VRChat.exe --watch-worlds --profile=0 --no-vr --enable-debug-gui --enable-sdk-log-levels --enable-udon-debug-logging -screen-width 1920 -screen-height 1080
```

:::danger Les nouveaux clients 'Build & Test' ne rejoignent pas les mondes rechargés

Si vous construisez et rechargez certains clients, puis choisissez 'Build & Test' pour ajouter plus de clients, ils risquent de ne pas être joints à la bonne pièce. Cependant, vous pouvez simplement réduire le nombre de clients à 0, puis 'Build & Reload' ou 'Recharger la dernière version compilée' pour les rejoindre tous à nouveau.
:::