

Voici les problèmes courants auxquels vous pourriez être confrontés lors de l'utilisation du SDK et comment les résoudre. Vous pouvez trouver une assistance supplémentaire sur notre [Base de connaissances d'aide](http://help.vrchat.com).

## Le panneau de contrôle de construction n'apparaît pas dans le menu déroulant du SDK VRChat !
Il existe deux raisons principales pour lesquelles cela peut se produire :

Assurez-vous d'utiliser la version recommandée pour VRChat. (Voir [Configuration du SDK](/sdk))

Vérifiez votre onglet de console pour vous assurer qu'il n'y a pas d'erreurs de compilation provenant de scripts ou de composants tiers. Si tel est le cas, vous devrez peut-être supprimer ces composants/scripts.

## J'ai téléchargé mon contenu mais je ne peux pas le voir dans le jeu !
Il y a quelques raisons possibles à cela. Voici quelques points à vérifier :

- Assurez-vous d'utiliser la [version correcte d'Unity](/sdk/current-unity-version).
- Assurez-vous d'utiliser le bon compte en jeu et de ne pas être connecté à un compte de plateforme.
- Vérifiez l'onglet `Gestionnaire de contenu` dans la fenêtre du panneau de contrôle pour voir si votre contenu est là.
- Vérifiez la console de l'éditeur pour voir s'il y a eu des erreurs lors du téléchargement.

## Je ne peux pas voir l'une des fenêtres mais il n'y a pas d'erreurs !
Dans de rares cas, les onglets Unity peuvent sortir de l'écran et devenir inaccessibles. Vous devrez supprimer certaines clés du registre pour ramener ces fenêtres sur votre écran.

1. Fermez Unity.
2. Appuyez sur la touche Windows et tapez `regedit`. Appuyez sur Entrée. Vous serez invité par l'UAC à autoriser l'accès administrateur.
3. Soyez très prudent dans `regedit` ! Cette application contient tous les paramètres de votre PC.
4. Trouvez la clé suivante : `Ordinateur\HKEY_CURRENT_USER\Software\Unity Technologies\Unity Editor 5.x`. Vous pouvez le faire en le collant dans la barre en haut de `regedit`, ou si vous n'avez pas de barre en haut de la fenêtre, en naviguant dans la liste des dossiers à gauche.
5. Supprimez TOUTES les clés de ce répertoire qui commencent par `VRC`, y compris `VRCSDK2` ou toute autre clé associée.
6. Fermez `regedit`.
7. Ouvrez à nouveau Unity. Vous devriez être prêt à continuer !

## J'obtiens des erreurs liées à SDK3 ou Udon dans un projet utilisant SDK2 ou VRC_SpatialAudioSource dans un projet utilisant SDK3 !

1. Suivez [les étapes correctes](/sdk/updating-the-sdk) pour supprimer votre SDK en fermant Unity et en supprimant tous les dossiers liés au SDK et leurs fichiers `.meta` associés.
2. Allez dans vos `Paramètres du projet` et trouvez `Symboles de définition de script` sous `Joueur > Autres paramètres`.
3. Supprimez les symboles qui ne sont pas associés au SDK sur lequel votre projet a été réalisé. Pour les projets réalisés avec SDK2, supprimez `UDON` et `VRC_SDK_VRCSDK3`. Pour les projets réalisés avec SDK3, supprimez `VRC_SDK_VRCSDK2`. Les symboles sont séparés par `;`. Ensuite, enregistrez les modifications en appuyant sur `Entrée`.
4. Importez le SDK correct dans le projet.

## J'ai un problème que la Base de connaissances ne résout pas et qui n'est pas mentionné ici !

Désolé pour cela ! Veuillez nous le faire savoir en [créant un ticket](http://help.vrchat.com/new) et nous vous aiderons.