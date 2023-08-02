

Si vous avez besoin de mettre à jour votre SDK, il est important de suivre ces étapes pour vous assurer que la mise à jour se déroule correctement et qu'aucun fichier ancien ou en conflit ne reste.

## Contrôle de version
Si vous savez comment l'utiliser, vous pouvez trouver utile d'utiliser un logiciel de contrôle de version tel que [Git](https://git-scm.com/) pour gérer votre projet. Vous n'avez pas besoin de télécharger votre dépôt sur Github ou un service similaire pour profiter des avantages du contrôle de version. Effectuez une validation avant de mettre à jour les SDK, juste pour être sûr.

## VRChat Creator Companion (VCC)
Il est extrêmement facile de maintenir votre SDK à jour avec le VCC. Consultez la documentation du [VRChat Creator Companion](https://vcc.docs.vrchat.com/guides/getting-started) pour apprendre à l'utiliser !

## Migration vers le VCC
Si vous souhaitez apprendre comment migrer votre projet pour utiliser le VCC, consultez le guide [ici](https://vcc.docs.vrchat.com/vpm/migrating).

## Mises à jour manuelles
Si vous utilisez le VCC, vous n'avez pas besoin de vous soucier des mises à jour manuelles.

## SDK3 hérité
:::caution 

Ces instructions s'appliquent uniquement aux utilisateurs de notre SDK hérité (`Assets\\VRCSDK`).\nSi votre SDK se trouve dans votre dossier `Packages` (`Packages\\com.vrchat.base`), ne suivez pas les instructions ci-dessous.
:::

**Pour le SDK3, vous devriez pouvoir mettre à jour en important simplement le nouveau SDK par-dessus l'ancien, également appelé mise à niveau sur place.** C'est particulièrement important pour les avatars SDK3, car vous risquez de perdre les comportements d'état de vos animateurs en cas de mise à jour incorrecte !

Si vous voulez être très prudent, sauvegardez toujours vos projets avant de mettre à jour le SDK.

### SDK3 - Monde
1. Fermez Unity.
2. Sauvegardez votre projet Unity ! Vous n'avez pas besoin de sauvegarder votre dossier Library, ces fichiers sont générés automatiquement par Unity.
:::caution Mise à niveau SDK3 avant 2020.3.2

**Cette étape est peu courante et vous n'aurez probablement pas besoin de la faire.** \n\nSi vous mettez à niveau à partir d'un SDK antérieur à 2020.3.2, allez dans le dossier `Assets` de votre projet et supprimez les dossiers `VRCSDK` et `Udon`, ainsi que les fichiers `VRCSDK.meta` et `Udon.meta`.
:::
3. Ouvrez votre projet Unity.
4. Importez le nouveau SDK3 - Monde par-dessus l'ancien.

### SDK3 - Avatars
:::danger Ne procédez pas à la "réinstallation par suppression" pour les avatars SDK3 !

***Si vous supprimez les dossiers du SDK avec Unity fermé et ouvrez Unity sans le SDK installé, vous perdrez les comportements d'état.*** Ils sont fragiles et ne persistent pas lors de mises à jour complètes par suppression. Assurez-vous de sauvegarder souvent vos projets et de sauvegarder/documenter vos configurations de comportements d'état.\n\nSi vous devez absolument effectuer une réinstallation complète par suppression de votre package d'avatars SDK3, sauvegardez d'abord votre projet. Vous devrez configurer vos comportements d'état à nouveau, alors assurez-vous de bien les documenter.
:::
1. Fermez Unity.
2. Sauvegardez votre projet Unity ! Vous n'avez pas besoin de sauvegarder votre dossier Library, ces fichiers sont générés automatiquement par Unity.
3. Ouvrez votre projet Unity.
4. Importez le nouveau SDK3 - Avatars par-dessus l'ancien. Si vous rencontrez des erreurs après l'importation, essayez de redémarrer Unity par la suite.
:::note Erreurs attendues lors de la mise à niveau SDK3 pour Avatar Dynamics

Il est normal d'avoir quelques erreurs lors de la première mise à niveau du SDK3 pour les avatars vers le SDK Avatar Dynamics. Cela est dû au fait que le SDK installe les packages Burst et Mathematics lors du processus d'installation, et qu'Unity se précipite un peu en les important prématurément.\n\nSi vous supprimez les erreurs ou redémarrez Unity, elles devraient disparaître.
:::

### SDK3 - Avatars - Créer un projet séparé
Si vous rencontrez des problèmes lors de la mise à niveau via le processus décrit ci-dessus, essayez ceci à la place :
1. Fermez Unity.
2. Créez un nouveau projet vide.
3. Importez le nouveau package d'avatars SDK3 dans ce projet.
4. Fermez ce projet Unity.
5. À l'aide de l'Explorateur (Ne pas ouvrir Unity encore !), supprimez les dossiers VRCSDK3 du projet que vous mettez à niveau. Jusqu'à ce que ce guide dise le contraire, ***ne pas ouvrir Unity.***
6. À partir de votre nouveau projet vide dans lequel vous avez importé le SDK, copiez les dossiers VRCSDK3 dans votre projet que vous mettez à niveau.
7. Une fois la copie terminée, ouvrez Unity et ouvrez votre projet mis à niveau. Vous pouvez supprimer le projet vide.

### Processus de mise à jour avancé

Si vous réinstallez le SDK dans un projet contenant un monde utilisant des configurations de déclencheur complexes, voici une façon plus sûre de mettre à jour votre SDK.

1. Fermez Unity.
2. Sauvegardez le projet dans un autre dossier (ne sauvegardez pas le dossier Library, ces fichiers sont générés automatiquement par Unity)
3. Supprimez les dossiers SDK et Plugins, ainsi que les fichiers .META correspondants
4. Créez un nouveau projet Unity vide
5. Installez le dernier SDK dans le projet vide
6. Copiez les dossiers SDK/Plugin nouvellement ajoutés et les fichiers .META correspondants du projet vide dans votre projet d'origine
7. Terminé. Maintenant, vous pouvez ouvrir votre projet mis à jour, et il n'y aura aucun crash, peu importe la complexité de votre configuration de déclenchement !

## Mise à jour d'Unity

Si vous mettez à jour à partir d'une version précédente d'Unity, nous avons un guide pour vous aider à effectuer la mise à jour vers notre dernière version prise en charge !