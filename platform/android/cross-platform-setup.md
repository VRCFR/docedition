

La configuration d'un monde ou d'un avatar multiplateforme est en réalité assez simple ! En bref, tout ce que vous avez à faire, c'est utiliser un projet dupliqué pour créer une version Android de la ressource et la télécharger avec le même ID de contenu que l'asset PC de VRChat. Le client se chargera de télécharger la version dont il a besoin.

Si vous avez besoin de plus de détails sur la manière de procéder correctement (et facilement), voici un bref guide.

# Dupliquer votre projet (obsolète)

:::caution

Avec l'avènement de la base de données des ressources v2, le passage d'une plateforme à une autre ne prend plus autant de temps ! La duplication de votre projet n'est plus vraiment nécessaire. Vous pouvez passer cette étape.

Vous pouvez également utiliser [EasyQuestSwitch](https://github.com/JordoVR/EasyQuestSwitch), qui facilite encore davantage le passage d'une plateforme à une autre.
:::

Nous supposerons que vous avez déjà configuré un projet VRChat PC avec votre monde ou votre avatar. Si ce n'est pas le cas, vous devrez d'abord configurer et créer votre projet pour PC. Vous pouvez également commencer par créer une version Android/Quest, mais c'est à vous de décider.

Une fois que vous avez votre projet prêt pour la construction et le téléchargement sur VRChat PC, allez-y et faites-le. Ce processus est identique à notre configuration standard.

Une fois que vous avez créé votre version VRChat PC, vous devrez dupliquer le projet pour la version Quest (Android). Pour ce faire, fermez Unity, **copiez votre dossier de projet et collez la copie ailleurs.** Vous dupliquez essentiellement votre projet. L'emplacement importe peu, tant qu'ils sont des projets séparés et distincts. Vous voudrez peut-être nommer le projet quelque chose comme `MonProjetVRChat-Quest` pour rester organisé.

Gardez à l'esprit que toutes les modifications que vous apportez à un projet doivent également être apportées à l'autre. S'il s'agit de quelque chose de simple comme déplacer un objet, vous pouvez simplement déplacer l'objet dans un projet, puis copier/coller les valeurs de transformation dans le second projet.

Pour les modifications plus complexes ou plus étendues, vous devrez peut-être redupliquer le projet ou être très prudent dans la manière de dupliquer les modifications.
# Configuration pour Quest
Ouvrez votre projet Quest dans Unity. Comme il s'agit d'une copie, vous ne devriez avoir apporté aucune modification. Cependant, cela va changer. Nous allons changer votre cible de construction en Android. Voici comment procéder :
![cross-platform-setup-dfca62a-VRChat_QuestContent_QuickStart.png](/img/cross-platform-setup-dfca62a-VRChat_QuestContent_QuickStart.png)

Voici quelques notes importantes :
- [Vous devez installer le SDK Android d'Unity](https://docs.unity3d.com/Manual/android-sdksetup.html). Sinon, l'option ne s'affichera pas.
- Bien que vous *puissiez* passer de Windows à Android et vice versa, **vous ne devriez probablement pas le faire.** Cela modifie les fichiers, vous souhaiterez probablement conserver une version simplifiée de votre monde pour Quest, et...
- Le passage à la plateforme Android peut prendre un **temps considérable**. Heureusement, si vous avez deux projets distincts, vous ne le faites qu'une fois. Si votre projet est volumineux ou comporte des dizaines d'avatars, vous voudrez probablement simplement exporter le contenu que vous souhaitez sous forme de préfabriqués ou de packages Unity, puis créer un nouveau projet Android vide.

:::note Serveur de cache local

Vous pouvez réduire le temps nécessaire pour passer d'une plateforme à une autre en utilisant le Cache Server d'Unity, que vous pouvez exécuter localement. [En savoir plus sur le serveur de cache ici](https://docs.unity3d.com/Manual/CacheServer.html). Gardez à l'esprit que cela peut prendre beaucoup d'espace disque.
:::

# Calibrage et optimisation
Maintenant que vous avez deux projets distincts configurés correctement, vous allez devoir commencer l'optimisation. **Vous ne pouvez pas sauter cette étape.** Le Quest est un casque puissant, mais bien moins puissant qu'un PC prêt pour la réalité virtuelle. Vous devrez consulter notre page [Optimisation du contenu pour Quest](/platforms/android/quest-content-optimization) pour voir ce que vous devez faire. Pour les mondes, cela signifie le baking de l'éclairage, la réduction de la complexité géométrique, l'évitement de la transparence et la réduction de la résolution des textures. Pour les avatars, cela signifie la suppression des composants superflus, des os superflus, la réduction de la complexité géométrique, l'évitement de la transparence et la réduction de la taille des textures.

Cela va prendre un certain temps et c'est censé être un défi. L'optimisation pour du matériel mobile est difficile ! Heureusement, il existe de nombreuses ressources disponibles, et même une simple recherche sur YouTube de "optimizing Unity for mobile" révèle de très bons contenus.

Vous pouvez également consulter certaines de nos documentations sur l'optimisation du contenu pour Oculus Quest.
- [Optimisation du contenu pour Quest](/platforms/android/quest-content-optimization)
- [Limites du contenu pour Quest](/platforms/android/quest-content-limitations)
- [Système de classement des performances des avatars](/avatars/avatar-performance-ranking-system)

:::caution Composants SyncVideoStream et SyncVideoPlayer

Les composants SyncVideoStream et SyncVideoPlayer ne sont actuellement pas pris en charge sur Quest. Les inclure dans un monde Quest provoquera des problèmes graves ! Il suffit de les supprimer de la version Quest. Cependant, avoir un lecteur vidéo uniquement dans la version PC peut également causer des problèmes. Si le Maître de l'instance est un utilisateur Quest, vous rencontrerez d'autres problèmes.

Bien que la possibilité de lire des vidéos synchronisées sur Quest soit un objectif à terme, nous vous recommandons de ne pas les utiliser tant que nous n'aurons pas de support officiel sur cette plateforme.
:::

# Téléchargement du contenu
Une fois que votre monde ou votre avatar est prêt, vous pouvez le télécharger ! Le processus de téléchargement est identique au processus de téléchargement pour VRChat PC, bien que le SDK vous mette en garde de manière plus agressive contre les problèmes de performances.

**Vous devez télécharger votre monde ou votre avatar avec le même ID de blueprint que celui utilisé pour la version PC de VRChat.** L'ID de blueprint est défini par un composant [Pipeline Manager](/sdk/vrcpipelinemanager) sur un objet de jeu, qui accompagne généralement un Descripteur de scène VRC, généralement sur votre préfabriqué VRCWorld. Cliquez sur le bouton "Détacher" pour modifier l'ID de blueprint, puis collez l'ID de la première version que vous avez téléchargée (vous pouvez également le trouver dans l'onglet "Gestionnaire de contenu" du panneau de contrôle du SDK de VRChat).

La version que vous téléchargez dépend de la plateforme de construction du projet d'origine. Si vous êtes sur un projet configuré pour Android, il sera téléchargé pour Quest. Si la cible de construction est Windows, vous téléchargez une version PC. C'est tout simplement cela - une fois que vous avez téléchargé, tout client qui visualise votre contenu communiquera avec nos serveurs de la manière suivante :

>"Hé, je suis un Oculus Quest et je veux ce contenu."
>"D'accord, voici une version pour Oculus Quest."

>"Hé, je suis un utilisateur VRChat PC et je veux ce contenu."
>"D'accord, voici la version VRChat PC."

Si un avatar n'est pas disponible pour la plateforme sur laquelle vous vous trouvez, vous verrez un avatar de remplacement indiquant la plateforme de cet utilisateur.

Si un monde n'est pas disponible pour la plateforme sur laquelle vous vous trouvez,