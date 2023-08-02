

## Exigence : Configurez d'abord le SDK !
Avant de commencer, assurez-vous d'avoir un [projet Unity avec le SDK configuré](/sdk).

Après avoir configuré le SDK, consultez notre exemple **exemple d'avatar**. Ouvrez votre projet d'avatar et allez dans
'VRChat SDK > Exemples > Avatar Dynamics Robot Avatar.'

![L'exemple d'avatar peut vous aider à comprendre à quoi peut ressembler un projet d'avatar VRChat complet.](/img/avatars/creating-your-first-avatar-3dfc191-Unity_YrUFLEWWDe.png)


:::note[Besoin d'aide ?]

La création de votre premier avatar peut être difficile. Si vous êtes bloqué, voici où vous pouvez obtenir de l'aide :
- Lisez notre documentation (vous êtes en train de le faire !)
- Consultez notre [forum officiel](https://ask.vrchat.com/)
- Rejoignez notre [serveur Discord](https://discord.com/invite/vrchat)

:::
## Étape 0 - Créez un modèle !
Bien que la plupart des utilisateurs choisissent de trouver un modèle (voir étape 1), il est TOTALEMENT possible de créer un modèle d'avatar à partir de zéro. Vous pouvez utiliser n'importe quel logiciel 3D de votre choix, tant qu'il prend en charge l'exportation d'un fichier FBX avec un armature ! Blender et Maya sont des choix très courants.

Soyons clairs : pour les personnes qui n'ont jamais modélisé en 3D auparavant, c'est le début d'un long voyage. Apprendre à modéliser en 3D est complexe, tout comme apprendre à rig et à texturer. La création d'un personnage riggé combine _toutes ces compétences_ !

Si vous choisissez de créer votre modèle, nous vous suggérons de commencer par quelque chose de simple. Même si vous ne semblez pas aussi flashy que les modèles préfabriqués, c'est _votre_ modèle, et vous pouvez faire ce que vous voulez avec.

Pour vous aider, voici un tutoriel centré sur VRChat créé par l'un de nos membres de la communauté :
- [Rainhet's Blender 3D Virtual Avatar Tutorial 2022](https://www.youtube.com/watch?v=OKWsUAIsgpg&list=PL2EEbgwoJzdsC9wfKA2ZO2kAf4HDqC8a8&index=1) - Le tutoriel de Rainhet est long et elle explique tout en détail pendant qu'elle travaille.
- [Rainhet's 3D Avatar Class](https://www.youtube.com/watch?v=w-yhjgnhaNw) - Une version plus ancienne de la série de tutoriels de Rainhet. Il existe également une [version de 10 minutes](https://www.youtube.com/watch?v=in9rNze4FD4) qui donne une vue d'ensemble du processus.

Si vous avez un tutoriel à suggérer, veuillez le soumettre à nos documents via la fonction "Modifier cette page".

## Étape 0.5 - Utilisez un créateur d'avatar !
Vous pouvez également essayer d'utiliser un créateur d'avatar ! Il en existe plusieurs de différentes complexités.

### Je veux essentiellement un créateur de personnage RPG, puis cliquez sur importer
[Page des systèmes d'avatar VRChat](https://hello.vrchat.com/avatar-systems) - Nous répertorions plusieurs créateurs faciles à utiliser sur cette page. Elle est régulièrement mise à jour.

### D'accord, donnez-moi quelques curseurs et la possibilité de peindre des choses
Vous voudrez peut-être vous tourner vers [VRoid Studio](https://vroid.com/en/studio), qui est également disponible sur Steam. Il s'agit d'un créateur de personnages sur le thème de l'anime destiné principalement à créer des modèles de style VTuber, mais il est très flexible ! Pour voir quelques exemples de ce qu'il peut faire, consultez le [subreddit VRoid](https://www.reddit.com/r/VRoid/).
:::note

VRoid Studio exporte des avatars au format **.vrm**, qui n'est pas nativement pris en charge par Unity ! Si vous souhaitez importer directement un modèle VRoid Studio pour l'utiliser dans VRChat, vous voudrez peut-être consulter le [convertisseur VRMtoVRChat](https://github.com/esperecyan/VRMConverterForVRChat) créé par la communauté pour les avatars .vrm. Assurez-vous de [lire la documentation de ce plugin](https://www.store.vket.com/ec/items/122/detail/) si vous l'utilisez.
:::
## Étape 1 - Trouvez un modèle
Sans doute la partie la plus importante, vous devez trouver un modèle 3D à utiliser comme avatar. Comme il s'agit de votre premier avatar, nous vous recommandons d'en trouver un sur le [Unity Asset Store](https://assetstore.unity.com/) car ils sont généralement entièrement riggés, ce qui signifie que vous n'avez rien de spécial à faire pour les télécharger. Si vous décidez