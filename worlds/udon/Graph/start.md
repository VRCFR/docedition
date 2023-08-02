

# Interface
Le Udon Node Graph est l'interface par défaut pour la création de programmes Udon. Cette section explique comment l'utiliser. Si vous souhaitez plonger directement dans des exemples, consultez la [Scène d'exemple Udon](/worlds/examples/udon-example-scene).

Vous pouvez ouvrir la fenêtre Udon Graph en utilisant l'élément de menu sous **VRChatSDK > Udon Graph**, ou en cliquant sur le bouton **Open Udon Graph** sur un composant UdonBehaviour.
![The Udon Window](/img/worlds/index-a1d7f43-open-graph.png)

:::caution Minimap
La minimap a été supprimée ! Maintenant que vous pouvez rechercher votre graphique par nom de groupe et nom d'événement, nous avons estimé que la minimap était plus distrayante qu'utile.
:::

Si vous ouvrez la fenêtre via la commande du menu, vous verrez l'écran de bienvenue, qui contient un journal des modifications et quelques paramètres.

Plusieurs graphiques peuvent être ouverts simultanément et vous pouvez basculer entre eux en utilisant les onglets en haut de la fenêtre du graphique.

Vous pouvez fermer des onglets en cliquant sur le X dans le coin de l'onglet que vous souhaitez fermer. Les onglets de graphique ne sont pas des onglets "réels" et rouvrent simplement chaque onglet au fur et à mesure que vous les sélectionnez. Cela signifie que changer d'onglets prend autant de temps que d'ouvrir des graphiques.

# Flux
Le flux de votre graphique définit les nœuds qui seront exécutés et l'ordre dans lequel ils le feront.
![](/img/worlds/index-f9c508c-simple-branching.png)

Les triangles dans l'image ci-dessus sont les ports _Flux_, et ils se déclenchent de gauche à droite, en suivant les nouilles qui les relient. Pour comprendre ce qui se passe dans les graphiques Udon et créer les vôtres, _suivez le flux_.

Il y a un interrupteur "Highlight flow" sur la barre supérieure, qui, lorsqu'il est activé, met en évidence les nœuds connectés via les arêtes de flux, vous permettant de voir rapidement comment le programme arrive au nœud particulier.
![](/img/worlds/index-2139dee-simple-flow-highlight.png)

Si le nœud n'a pas de connexions de flux, rien ne se passera.

Dans le graphique ci-dessus :
1. L'événement _Start_ se déclenche lorsque le monde se charge.
2. La branche se déclenche ensuite. Elle vérifie la valeur de sa case à cocher, puis déclenche soit le chemin *True*, soit le chemin *False*.
3. Si la valeur est True, nous déclenchons le nœud supérieur, qui envoie un événement personnalisé appelé "Hello".
4. Sinon, nous enverrons un événement personnalisé appelé "Goodbye".

Ce n'est pas grave si vous ne savez pas encore ce que signifie **Envoyer un événement personnalisé**. Apprendre à lire le flux d'un graphique est la première étape pour comprendre ce qu'ils font.

# Création de nœuds
Les nœuds sont les boîtes qui représentent les méthodes que vous pouvez déclencher. La construction d'un graphique consiste à créer et à relier des nœuds pour créer un programme.

Il existe plusieurs façons de créer des nœuds :
  * [Raccourcis clavier](#raccourcis-clavier)
  * [Actions de glisser-déposer](#glisser-déposer-pour-les-objets-de-jeu-et-les-composants)
  * [Menus de recherche](#recherche-de-nœuds)

## Raccourcis clavier
Maintenez enfoncée l'une des touches suivantes, puis cliquez n'importe où sur le graphique pour créer le nœud correspondant :
* `1` : float
* `2` : Vector2
* `3` : Vector3
* `4` : Vector4
* `+` : addition de float
* `-` : soustraction de float
* `=` : comparaison d'égalité de float
* `b` : branche
* `shift+b` : bloc

## Autres raccourcis clavier :
* Maintenez enfoncée la touche "C", puis cliquez sur une constante pour la convertir en variable.
* Shift+A aligne les nœuds sélectionnés.
* Maintenez la touche Ctrl+G enfoncée pour regrouper rapidement.
* L+cliquez pour enregistrer la valeur du nœud sélectionné.
* Maintenez enfoncée la touche "Shift+F", puis cliquez sur un nœud qui produit un type de tableau pour générer automatiquement une boucle foreach.
De nombreuses de ces fonctionnalités sont également disponibles dans les menus contextuels (clic droit) de leurs nœuds respectifs.
![La manière la plus simple de créer des boucles for !](/img/worlds/index-87b33a4-for-loop.gif)

## Glisser-déposer pour les objets de jeu et les composants
Si vous souhaitez ajouter de l'interactivité à un objet de jeu ou à un composant, vous pouvez le faire glisser et le déposer depuis votre hiérarchie sur le graphique. Par exemple, vous pouvez faire glisser et déposer un composant Light en le saisissant depuis le titre 'Light' sur le graphique.
![Une façon facile d'obtenir une référence à un composant Light afin de pouvoir y jouer.](/img/worlds/index-6238d1e-light-component.jpg)
La création de nœuds via glisser-déposer de cette manière crée des variables liées à votre objet de jeu ou à votre composant. Vous verrez donc une nouvelle variable apparaître dans la fenêtre des variables, ainsi qu'un nœud qui est en fait un nœud "Get Variable" qui est automatiquement configuré pour obtenir votre nouveau composant.

## Glisser-déposer pour les variables
Vous pouvez créer des variables de n'importe quel type en cliquant sur le bouton "+" dans le volet Variables de la barre latérale du graphique. Ensuite, vous pouvez faire glisser le nom de la variable sur le graphique pour créer un nœud "Get Variable", maintenir la touche **Ctrl** enfoncée tout en faisant glisser pour créer un nœud "Set Variable", ou maintenir la touche **Alt** enfoncée pour créer un nœud "On Variable Changed".

## Recherche de nœuds
Appuyez sur la touche **Espace** pour ouvrir la recherche rapide, puis saisissez les premières lettres de la classe avec laquelle vous souhaitez interagir.
![](/img/worlds/index-08df7d3-gameobject-search.png)

Cette méthode de recherche fonctionne mieux si vous connaissez les classes de base et les types d'objets d'Unity. Il existe d'autres moyens de recherche, voir: [Recherche de nœuds](/worlds/udon/graph/searching-for-nodes)

# Compilation du graphique
Le graphique se compile automatiquement en arrière-plan à intervalles réguliers. Lorsque cela se produit, vous verrez un flash dans le coin supérieur droit de votre graphique, et la boîte d'état deviendra verte si tout s'est bien passé, ou rouge s'il y a un problème. Dans les deux cas, vous pouvez cliquer sur la boîte d'état pour voir le code d'assemblage qui a été généré, ou les erreurs s'il y a un problème.
![The status box shows 'OK' and we can see the Variables declared at the top of this Assembly.](/img/worlds/index-fc0a2c0-assembly.png)

# Exécution du graphique
Il existe deux façons d'exécuter les graphiques de votre scène avant de les télécharger sur VRChat.

## Exécution dans l'éditeur
Vous pouvez utiliser le bouton Lecture d'Unity pour exécuter votre scène directement dans l'éditeur afin de tester certains graphiques. Cela fonctionnera pour quelques méthodes et logiques simples, mais les éléments suivants ne fonctionneront pas comme prévu :
* Variables synchronisées et événements réseau
* L'objet VRCPlayerAPI - utilisation des stations, déclenchement d'événements Interact, tout ce qui concerne les avatars.

## Construire et tester
Utilisez la fenêtre VRChat SDK pour effectuer des tests locaux. Cela prend un peu plus de temps car il regroupe votre contenu dans un monde hors ligne et lance le client VRChat réel pour vous donner un avatar capable d'interagir avec des objets et des demandes VRCPlayerAPI.
![The simplest way to test Sync features is to launch 2 local clients.](/img/worlds/index-32da932-local-testing-2.png)
Pour tester les variables synchronisées et les NetworkEvents, vous aurez besoin de deux clients - vous pouvez utiliser le champ 'Number of Clients' pour lancer jusqu'à 8 clients locaux qui se lanceront dans un monde de test privé. Ils auront tous le même DisplayName, mais ils seront reconnus comme des joueurs distincts, vous pourrez donc tester vos interactions.
:::danger Définir le chemin de votre client local

Si 'Force Non-VR' ne fonctionne pas pour vous, passez à l'onglet 'Settings' de la fenêtre VRChat SDK et définissez le chemin de votre client VRChat pour qu'il pointe vers votre installation VRChat réelle.
:::

![](/img/worlds/index-6d24