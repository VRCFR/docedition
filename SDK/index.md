

## Exigences et téléchargements
Il existe plusieurs façons de télécharger le SDK VRChat.
- Cliquez [ici](https://vrchat.com/download/vcc) pour télécharger le [VRChat Creator Companion](https://vcc.docs.vrchat.com/). C'est la manière la plus simple de commencer. Le Creator Companion peut installer automatiquement l'Unity Editor, le SDK Worlds et le SDK Avatars pour vous.
- Alternativement, vous pouvez utiliser l'un de nos [projets modèles sur GitHub](https://vcc.docs.vrchat.com/guides/using-project-template-repos). Si vous n'utilisez pas le Creator Companion, vous devrez également télécharger la [version actuelle d'Unity](/sdk/current-unity-version). Nous recommandons fortement d'utiliser Unity Hub pour télécharger Unity, disponible [ici](/sdk/current-unity-version).


## Étape 0 - Installation d'Unity
Si vous avez déjà Unity installé et opérationnel, vous pouvez passer à l'[étape 1](#section-step-1-creating-a-project). Le [Creator Companion](https://vcc.docs.vrchat.com/) installe automatiquement Unity pour vous.

Si vous souhaitez installer Unity vous-même, consultez la page [Version actuelle d'Unity supportée](/sdk/current-unity-version) et installez la version d'Unity actuellement soutenue par VRChat, idéalement en utilisant Unity Hub.


## Étape 1 - Création d'un projet
Pour notre premier projet, nous supposerons que vous créez du contenu pour Windows PC. Si vous souhaitez créer du contenu pour VRChat sur Quest, consultez [Configuration d'Unity pour la création de contenu Quest](/platforms/android/setting-up-unity-for-creating-quest-content).

La manière la plus simple de créer un projet prédéfini est d'utiliser le [VRChat Creator Companion !](https://vcc.docs.vrchat.com/guides/getting-started) Nous vous recommandons vivement d'utiliser le VRChat Creator Companion à cet effet. Sinon, vous devrez effectuer plusieurs étapes supplémentaires qui pourraient être sujettes aux erreurs.

Quelques conseils rapides :

* Sauvegardez vos projets sur un disque de stockage de masse avec beaucoup d'espace - les projets Unity peuvent devenir très volumineux, en particulier si vous utilisez des logiciels de versionnage.
* N'utilisez pas un seul projet pour de nombreux avatars ou mondes différents. C'est un moyen rapide de rendre les futures migrations très fastidieuses !
* Si vous savez comment utiliser des logiciels de contrôle de version tels que [Git](https://git-scm.com/) ou [Plastic SCM](https://www.plasticscm.com/), utilisez-les ! Cela facilite grandement le retour en arrière des modifications qui cassent votre projet.
* Si vous ne savez pas comment les utiliser, vous devriez apprendre ! Ils sont formidables. Malheureusement, un tutoriel Git est bien au-delà de la portée de notre documentation 😰

Vous pouvez créer un projet manuellement si vous le souhaitez, mais vous devrez de toute façon utiliser le [Creator Companion](https://vcc.docs.vrchat.com/) plus tard pour installer le SDK (à moins que vous n'ayez commencé avec l'un de nos [modèles de référentiel](https://vcc.docs.vrchat.com/guides/using-project-template-repos).

Si vous utilisez Unity Hub :
* Ouvrez Unity Hub (ou simplement l'éditeur si vous avez choisi cette option).
* Créez un nouveau projet, **réglez-le sur 3D et enregistrez-le**.
* N'utilisez pas HDRP ou URP. Nous ne les utilisons pas.

## Étape 2 - Ouvrir votre projet
Quelle que soit la manière dont vous l'avez créé, vous pouvez maintenant ouvrir votre projet. Si votre projet ne s'affiche pas, cliquez sur "Ajouter" dans l'écran du projet et sélectionnez-le. Si vous utilisez Unity Hub, cliquez sur "Ouvrir" en haut à droite, puis sélectionnez le répertoire où se trouve votre projet.

Après l'ouverture du projet, vérifiez la barre de titre pour vous assurer qu'elle se termine par `PC, Mac & Linux Standalone <DX11>`. Si ce n'est pas le cas, allez dans `Fichier > Paramètres de construction...`, sélectionnez `PC, Mac & Linux Standalone`, puis cliquez sur `Changer de plateforme` en bas à gauche.

Si vous créez du contenu pour VRChat pour Meta Quest ou Android, vous devez également créer pour Android. Consultez notre documentation [Android](/platforms/android/index.md) pour plus de détails.

## Étape optionnelle 3 - Installation du SDK
Si vous n'avez pas utilisé le VCC pour configurer votre projet, vous devrez installer le SDK. Faites-le via le [VRChat Creator Companion](https://vcc.docs.vrchat.com/guides/getting-started).

Si des erreurs surviennent, même avec un projet vide tout juste créé, [veuillez contacter notre équipe de support](https://vrch.at/support).

## Étape 4 - Connexion
Pour utiliser le SDK, vous devrez vous connecter. Pour ce faire, rendez-vous à `VRChat SDK > Afficher le panneau de contrôle > Authentification`. Vous pouvez vous connecter à votre compte VRChat ici.

N'oubliez pas que vous devez posséder un compte VRChat avec au moins une "Nouvelle note de confiance utilisateur" [Trust Rank](https://docs.vrchat.com/docs/vrchat-safety-and-trust-system) pour pouvoir télécharger du contenu. Vous ne pouvez pas utiliser un compte Steam, Oculus ou Viveport pour télécharger du contenu.

### Que faire ensuite ?
Votre projet est prêt ! Vous pouvez passer à la [Création de mondes](/worlds) ou à la [Création d'avatars](/avatars).