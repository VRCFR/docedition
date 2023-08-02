

# Qu'est-ce que le débogage ?
Le débogage est un moyen d'apprendre ce qui se passe en interne dans le client VRChat et dans votre monde. C'est une compétence essentielle à développer pour la programmation en général et pour la création de vos mondes.

# Journaux VRChat
Lorsque vous utilisez le client VRChat, il enregistre des journaux sur ce qui se passe, comme les mondes que vous visitez, les erreurs que vous rencontrez et d'autres informations en arrière-plan, dans des fichiers texte sur votre machine.

# Affichage de vos journaux dans le client
Lorsque vous lancez VRChat avec l'interface de débogage activée (voir ci-dessous), vous pouvez activer des superpositions de débogage spéciales en mode bureau et en réalité virtuelle. Pour afficher vos messages de journal au fur et à mesure qu'ils apparaissent, appuyez sur RShift + Backtick + 3. Vous pouvez trouver tous les raccourcis disponibles pour différentes superpositions de débogage sur la page [Clavier et souris](https://docs.vrchat.com/docs/keyboard-and-mouse).

# Affichage de vos journaux dans un éditeur de texte
Vous pouvez consulter ces fichiers pendant ou après une session VRChat en les recherchant sur votre disque et en les ouvrant. Ils sont généralement enregistrés dans le dossier suivant, avec votre nom d'utilisateur d'ordinateur à la place de 'YourName':

`C:\Users\YourName\AppData\LocalLow\VRChat\VRChat`

Dans ce dossier, vous trouverez d'autres dossiers et quelques fichiers portant des noms tels que :
`output_log_08-55-48.txt`

Ce sont vos fichiers de journal - un nouveau fichier est créé à chaque fois que vous lancez VRChat, avec un horodatage pour que les noms soient uniques. Vous pouvez les ouvrir dans n'importe quel navigateur de texte pour trouver des informations détaillées sur ce qui s'est passé pendant votre session.

# Options de journal
Lorsque vous *Construisez et testez* votre monde en utilisant le bouton dans le panneau de contrôle VRChat, Unity lance VRChat et transmet quelques arguments de ligne de commande qui activent des fonctionnalités de débogage pour obtenir toutes les informations possibles. Lorsque vous lancez VRChat d'une autre manière, vous n'aurez que des journaux limités. Pour copier la manière dont *Construisez et testez* lance VRChat, vous voudrez transmettre quelques indicateurs. Vous pouvez le faire de plusieurs manières différentes.

# Fichiers batch
Pour lancer VRChat avec des options spéciales, vous pouvez utiliser un fichier batch. Il s'agit simplement d'un fichier texte que vous créez avec quelques commandes spéciales.
1. Créez un nouveau fichier texte appelé `debug.bat` juste à côté de VRChat.exe sur votre machine.
2. Ajoutez cette ligne au fichier : `VRChat.exe --no-vr --enable-debug-gui --enable-sdk-log-levels --enable-udon-debug-logging`
3. Enregistrez le fichier et exécutez-le pour tester !

Cette commande active 3 indicateurs pour un journal supplémentaire, et force également VRChat à contourner la réalité virtuelle pour les tests sur ordinateur de bureau. Vous pouvez transmettre d'autres options - vous pouvez inclure n'importe lequel des indicateurs de la page [Options de lancement de VRChat](https://docs.vrchat.com/docs/launch-options) ainsi que les [arguments de ligne de commande Unity Standalone Player](https://docs.unity3d.com/Manual/CommandLineArguments.html).

Par exemple, voici un fichier batch que j'utilise qui lance mon profil VRChat secondaire et force une résolution d'écran de 720p :
`VRChat.exe --profile=1 --no-vr --enable-debug-gui --enable-sdk-log-levels --enable-udon-debug-logging -screen-width 1280 -screen-height 720`

# Options de lancement Steam
Si vous utilisez la version Steam de VRChat, vous pouvez également définir des options de lancement permanentes. Nous ne recommandons généralement pas cela car cela rend plus difficile le passage entre les lancements normal et de débogage, mais voici comment procéder :

1. Dans votre bibliothèque Steam, faites un clic droit sur l'entrée VRChat et choisissez 'Propriétés'.
2. Dans l'onglet 'Général', appuyez sur le bouton 'Définir les options de lancement'.
3. Dans le champ qui apparaît, vous pouvez saisir les indicateurs spécifiques à VRChat que vous souhaitez toujours activer, comme `--enable-debug-gui --enable-udon-debug-logging` pour avoir toujours l'interface de débogage et le débogage Udon activés.

# Détection des erreurs Udon
Lorsqu'un UdonBehaviour rencontre un problème majeur lors de son exécution dans le client, il se désactive. Si vous regardez les journaux dans le client, vous verrez une entrée comme ceci :
`[UdonBehaviour] An exception occurred during Udon execution, this UdonBehaviour will be halted.`
Pour en savoir plus sur ce qui s'est passé, ouvrez vos fichiers de journal en suivant les instructions ci-dessus dans la section *Affichage de vos journaux*, et recherchez le mot-clé 'halted'. Vous y trouverez plus d'informations sur ce qui s'est passé, comme ceci :
```
2020.08.28 17:40:51 Erreur      -  [UdonBehaviour] An exception occurred during Udon execution, this UdonBehaviour will be halted.
VRC.Udon.VM.UdonVMException: An exception occurred in an UdonVM, execution will be halted. ---> VRC.Udon.VM.UdonVMException: An exception occurred during EXTERN to 'VRCSDK3VideoComponentsBaseBaseVRCVideoPlayer.__GetTime__SystemSingle'. ---> System.NullReferenceException: Object reference not set to an instance of an object.
  at VRC.SDK3.Internal.Video.Components.AVPro.AVProVideoPlayerInternal.GetTime () [0x00000] in <00000000000000000000000000000000>:0 
  at VRC.Udon.Wrapper.Modules.ExternVRCSDK3VideoComponentsBaseBaseVRCVideoPlayer.__GetTime__SystemSingle (VRC.Udon.Common.Interfaces.IUdonHeap heap, System.UInt32[] parameterAddresses) [0x00000] in <00000000000000000000000000000000>:0 
```
Ouch, tant d'informations ! Les informations clés se trouvent dans la deuxième ligne : `
An exception occurred during EXTERN to 'VRCSDK3VideoComponentsBaseBaseVRCVideoPlayer.__GetTime__SystemSingle'. ---> System.NullReferenceException: Object reference not set to an instance of an object.`
Cela nous indique que notre monde essaie d'accéder à quelque chose qui n'existe pas. Plus précisément, nous essayons d'accéder à un VideoPlayer alors qu'il n'y en a pas d'assigné. C'est ce que signifie ` Object reference not set to an instance of an object`, et `VRCSDK3VideoComponentsBaseBaseVRCVideoPlayer.__GetTime__SystemSingle` nous indique que cela s'est produit lorsque nous avons essayé d'appeler *GetTime* sur un *VRCVideoPlayer*. Une fois que vous êtes à l'aise avec la lecture des journaux, ce genre d'informations est inestimable. Je peux maintenant me rendre sur le graphe qui essaie d'appeler VRCVideoPlayer.GetTime et m'assurer qu'il est connecté à un VideoPlayer.

# Diagnostiquer les problèmes d'Udon
Si vous êtes dans une situation où Udon ne fait pas ce que vous voulez, une bonne façon de diagnostiquer le problème est d'ajouter des nœuds `Debug Log` avec un texte unique. Placez-les juste avant d'essayer de faire quelque chose d'important, mettez-les juste après avoir tenté de faire quelque chose d'important, et placez-les n'importe où qui pourrait être important en général. Ensuite, lorsque vous exécutez votre UdonBehaviour, vous pouvez observer le journal pour voir jusqu'où il arrive et s'il fait ce que vous attendez.