

![ClientSim in Unity Editor](/images/editor-screenshot.png)

Le simulateur de client VRChat, ou ClientSim pour faire court, est un outil qui vous permet de tester directement vos mondes VRChat SDK3 dans Unity&nbsp;! Vous pouvez examiner l'état de tous les objets pour vérifier les choses directement.

## Fonctionnalités

- Déboguer tout dans Unity.
- Inspecter les variables Udon en mode lecture.
- Contrôleur pour joueur sur ordinateur de bureau.
- Ramasser, utiliser les interactions, les interfaces utilisateur et les stations.
- Supprimer les objets uniquement pour l'éditeur en mode lecture.

## Configuration

### Exigences

- Unity 2019.4.29-31
- Versions des packages des SDK [VRChat Base](https://github.com/vrchat/packages/tree/main/packages/com.vrchat.base) et [Worlds](https://github.com/vrchat/packages/tree/main/packages/com.vrchat.worlds) 

### Installation

> Remarque&nbsp;: cela sera beaucoup plus facile avec la prochaine version bêta ouverte du VRChat Creator Companion, Coming Soon™
>
- Dans votre projet, ouvrez le Gestionnaire de packages Unity, cliquez sur le bouton + et choisissez "Ajouter un package depuis un URL Git...".
    - Entrez l'URL suivante : `https://github.com/vrchat/packages.git?path=/packages/com.vrchat.base#vcc`. Ensuite, attendez que le package s'importe ou appuyez sur Ctrl+R pour actualiser si vous avez désactivé l'actualisation automatique.
    - Cliquez à nouveau sur le bouton + et ajoutez cette URL Git : `https://github.com/vrchat/packages.git?path=/packages/com.vrchat.worlds#vcc`
    - Appuyez une dernière fois sur le bouton + et ajoutez cette URL&nbsp;: `https://github.com/vrchat-community/ClientSim.git?path=/ClientSim_UnityProject/Packages/com.vrchat.ClientSim#issue-12-make-docs`

### Premiers pas

- Ouvrez votre scène de monde VRChat
- Appuyez sur lecture dans Unity
- Testez votre monde

## Apprenez-en davantage sur le fonctionnement de tous les systèmes dans la section [Systèmes](systems)

### Nouvelles fonctionnalités dans ClientSim par rapport à CyanEmu
- Manipulation des objets ramassables avec I, J, K, L, U, O, la roulette de la souris et la manette de jeu.
- Saisie basée sur la disposition du clavier plutôt que sur des touches spécifiques.
- Les joueurs locaux et distants ont maintenant des avatars humanoïdes, prise en charge des os de l'avatar (mais pas des systèmes d'avatar complets).
- Affichage et configuration directe des données du joueur - valeurs de locomotion, réglages audio de la voix et de l'avatar, santé en combat.
- Déverrouillez la souris en maintenant la touche Tab enfoncée - vous pouvez ainsi mettre en évidence des objets décentrés.
- Un pointeur s'affiche lorsque vous pouvez interagir avec un élément d'interface utilisateur.
- Nouvelles options d'exécution&nbsp;: démarrer en tant que non-maître, inverser la souris, afficher les info-bulles, modifier l'échelle du joueur, définir le taux de rafraîchissement cible, retarder le démarrage pour simuler le chargement.
- Nouveau menu en mode lecture avec un style mis à jour, des boutons d'informations sur le joueur et des paramètres.
- Nouveaux boutons dans la fenêtre Paramètres pour mettre à jour les paramètres du projet, ne se fait plus sans le consentement de l'utilisateur.
- Mise en évidence des maillages qui correspond à Android.
- Emplacement de l'info-bulle mis à jour pour correspondre à l'application cliente.
- Meilleure prise en charge de la manette de jeu.
- Prise en charge de la désactivation du rechargement de domaine pour entrer en mode lecture sans délai - notez qu'il existe un bug Unity qui empêche les événements de l'interface utilisateur de fonctionner s'ils ne sont pas définis sur "Editor and Runtime".
- Tests automatisés - vous devez l'activer spécifiquement pour qu'il n'affecte pas votre projet. Documentation à venir.

### Problèmes connus

- La modification manuelle des paramètres du projet Unity pour activer le nouveau système de saisie peut ne pas permettre une saisie correcte. Les utilisateurs doivent utiliser les boutons de la fenêtre Paramètres de ClientSim.
- Physics.RaycastNonAlloc ne renvoie parfois pas les colliders qui ont bougé et n'ont pas de rigidbodies.
- En quittant le mode lecture, des exceptions peuvent être générées occasionnellement en raison de l'ordre dans lequel les objets sont détruits.
- Le shader de mise en évidence ne fonctionne pas sur Mac (Metal).

## Droits d'auteur

Droits d'auteur (c) 2021 VRChat
Voir License.md pour les informations complètes sur l'utilisation

## Crédits

Basé sur [CyanEmu](https://github.com/CyanLaser/CyanEmu) de [CyanLaser](https://github.com/CyanLaser), qui a également réalisé cette version.