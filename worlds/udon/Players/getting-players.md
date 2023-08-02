
### Networking.get LocalPlayer
*VRCPlayerApi*
:::note

Veuillez noter que cette fonction est membre de la classe Networking, mais elle est incluse ici.
:::
Le joueur local est le joueur sur lequel s'exécute actuellement ce script Udon, autrement dit, le joueur local c'est *vous*. Il est très important de se connaître soi-même !

### GetPlayerCount
*int*
Retourne le nombre réel de joueurs dans l'instance lorsqu'il est appelé.

### GetPlayers
*VRCPlayerApi[]*
C'est ainsi que vous obtenez tous les joueurs de votre monde afin de pouvoir les parcourir avec une boucle "for" et appliquer des paramètres, effectuer des modifications, rechercher un nom particulier, etc. Pour l'utiliser, vous *devez d'abord créer un tableau de VRCPlayerApi*. [Voici un package Unity](https://drive.google.com/file/d/1i9eHLqD25WTMAFnDay1kwg1nE-0iyLrO/view?usp=sharing) avec un exemple fonctionnel.
![Le strict minimum pour appeler GetPlayers. Une meilleure approche serait de construire VRCPlayerApi[] comme une variable afin de pouvoir le réutiliser.](/img/worlds/getting-players-506acb6-getplayers.png)
### GetPlayerById
*int*
Obtient un objet VRCPlayerApi pour l'ID de joueur donné s'il existe.

### get playerId
*int*
Obtient l'ID du joueur mis en cache, appelle GetPlayerId s'il n'a pas encore été mis en cache.

### GetPlayerId
*int*
Obtient l'ID réseau du joueur à partir de la source.

## Système de tags de joueur
Ce système est une façon rapide et simple d'attribuer des chaînes de caractères aux joueurs sans créer vos propres variables et collections.

### SetPlayerTag / GetPlayerTag
Set : *string, string*
Get : *string*
Définit une variable de chaîne de caractères que vous pouvez rechercher ultérieurement. Par exemple, vous pourriez définir le "rôle" d'un joueur dans un jeu de cuisine comme "chef" ou "client". Ensuite, vous pourriez utiliser GetPlayerTag pour récupérer "rôle" et obtenir soit "chef", soit "client".

### ClearPlayerTags
*VRCPlayerApi*
Supprime tous les tags que vous avez définis pour un joueur.

### GetPlayersWithTag
**A BESOIN D'UNE CORRECTION**
Ne fonctionne actuellement pas car elle renvoie une liste. Je vais corriger et mettre à jour. Vous pourrez passer un tableau d'objets VRCPlayerApi et un tag à la méthode qui remplira le tableau avec les joueurs qui ont ce tag défini.

Les méthodes suivantes sont obsolètes - elles ne fonctionnent pas dans SDK3 et seront supprimées à l'avenir :
### SetSilencedToTagged
### SetSilencedToUntagged
### ClearSilence