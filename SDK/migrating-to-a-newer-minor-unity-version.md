
De temps en temps, VRChat se met à jour au sein des grandes versions d'Unity.

La mise à niveau de vos projets entre ces versions est plus facile que lors des changements de versions majeures. 

## Étapes de mise à niveau

### Étape 1 - Installer la nouvelle version d'Unity

Fermez tous vos projets ouverts.

Consultez la [Version d'Unity actuellement supportée](/sdk/current-unity-version) et installez la nouvelle version d'Unity via Unity Hub.

Bien que nous indiquions l'installateur autonome sur cette page, vous devriez *vraiment* utiliser Unity Hub. Nous supposons que vous l'utilisez dans ces étapes.

### Étape 2 - Faire une copie de votre projet

Créez toujours une sauvegarde de votre projet avant d'effectuer de gros changements potentiellement destructeurs. Vous pouvez le faire en faisant simplement une copie du dossier du projet et en migrant cette copie au lieu de votre projet principal. De cette façon, si cela se passe mal, vous pouvez le supprimer et recommencer.

Si vous êtes un utilisateur avancé et que vous savez comment utiliser un gestionnaire de versions comme [git](https://git-scm.com/), vous devriez certainement l'utiliser. Cela facilite la gestion de sauvegardes comme celle-ci.

### Étape 3 - Ouvrir votre projet

Ouvrez la copie de votre projet dans la nouvelle version.

Vous obtiendrez quelques avertissements de mise à niveau. C'est normal ! Cliquez sur "Oui", "OK" ou sur le bouton "affirmatif" correspondant.

Après un certain temps, votre migration sera terminée. Et voilà !

### Étape 4 - Mettre à jour votre SDK

Les mises à jour du SDK ne sont pas toujours nécessaires lors de mises à niveau mineures de version. Si elles sont nécessaires, c'est à ce moment-là que vous le feriez.

Fermez votre projet après la migration et utilisez le [VCC](https://vcc.docs.vrchat.com/) pour mettre à jour votre SDK.

## Conseils et autres informations

Voici quelques conseils supplémentaires qui pourraient vous aider dans le processus.

### Avertissements Unity

Il existe quelques avertissements Unity qui peuvent apparaître pendant la migration et que vous pouvez ignorer en toute sécurité. Voici quelques-uns que vous pourriez rencontrer.
![migrating-to-a-newer-minor-unity-version-f3995eb-image_10.png](/img/sdk/migrating-to-a-newer-minor-unity-version-f3995eb-image_10.png)

![migrating-to-a-newer-minor-unity-version-b20553b-image_11.png](/img/sdk/migrating-to-a-newer-minor-unity-version-b20553b-image_11.png)

### Nettoyer la copie

Si votre projet est volumineux, la migration peut prendre beaucoup de temps. Il existe quelques dossiers que vous n'avez pas besoin de migrer si le projet est particulièrement volumineux. Vous pouvez supprimer en toute sécurité ces dossiers de la copie.

Vous n'aurez probablement pas tous ces dossiers dans votre projet.
```text
/Library/
/Temp/
/Obj/
/Build/
/Builds/
/Logs/
/UserSettings/
```

## Avertissements de version

Le SDK peut vous avertir que vous êtes sur la mauvaise version, même si vous savez que vous êtes sur la bonne.
![migrating-to-a-newer-minor-unity-version-1b8194d-2022-11-30_10-35-54_chrome.png](/img/sdk/migrating-to-a-newer-minor-unity-version-1b8194d-2022-11-30_10-35-54_chrome.png)
C'est normal ! Si vous savez avec certitude que vous êtes sur la bonne version, vous pouvez ignorer ce message.