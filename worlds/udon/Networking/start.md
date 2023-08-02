
:::note[Aperçu]

Les expériences multijoueurs sont au cœur de VRChat, il est donc essentiel de créer un monde qui réagit aux joueurs et synchronise les données entre eux.

Cette page présente les concepts qui alimentent notre système de mise en réseau. Une fois que vous avez compris les bases, vous pouvez approfondir les détails spécifiques :
* [Composants réseau](/worlds/udon/networking/network-components)
* [Spécifications et astuces réseau](/worlds/udon/networking/network-details)
:::

# Aperçu : Comment fonctionne la mise en réseau dans Udon

<iframe class="embedly-embed" src="//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FMb6ZYBEhxiI%3Flist%3DPLe9XHNvXcouQjg5GULWGLj1tMzeythnQi&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DMb6ZYBEhxiI&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FMb6ZYBEhxiI%2Fhqdefault.jpg&key=f2aa6fc3595946d0afc3d76cbbd25dc3&type=text%2Fhtml&schema=youtube" width="854" height="480" scrolling="no" title="YouTube embed" frameborder="0" allow="autoplay; fullscreen" allowfullscreen="true"></iframe>

Les trois concepts principaux utilisés pour la mise en réseau dans Udon sont les **Variables**, les **Événements** et la **Propriété**.

Les **variables** sont des conteneurs de valeurs, telles qu'un nombre, un ensemble de couleurs ou une position 3D.
Les **événements** sont des événements qui se produisent à un moment donné.
La **propriété** est le système qui décide quel utilisateur peut mettre à jour une variable, qui est ensuite envoyée à tous les autres utilisateurs.

Pour un tableau des scores dans un jeu, vous pouvez utiliser une variable pour stocker et mettre à jour les scores des utilisateurs, et un événement pour déclencher des feux d'artifice pour le gagnant.

# Propriété

Par défaut, les objets dans un monde sont *locaux*. Cela signifie qu'un objet que vous ramassez **ne bouge que pour vous**, personne d'autre ne le voit bouger. Pour synchroniser l'objet, vous devez indiquer à VRChat que vous souhaitez qu'il soit un **objet en réseau**.

Pour rendre un objet **en réseau**, vous pouvez lui ajouter un composant UdonBehaviour et/ou un composant VRC Object Sync.

Le premier joueur qui ouvre un monde devient le propriétaire de tous les objets en réseau. Il peut apporter des modifications à ces objets et les modifications seront envoyées à tous les autres. Lorsque vous changez le propriétaire d'un objet, le nouveau propriétaire est responsable des données réseau et tous les autres écouteront ses modifications.

## Exemple : L'objet en réseau le plus simple

Si vous avez un objet 3D avec un rendu et un collider, vous pouvez facilement en faire quelque chose que les gens peuvent ramasser et synchroniser.

Tout ce que vous avez à faire est d'ajouter un composant VRCPickup et un composant VRCObjectSync à son GameObject.
![](/img/worlds/udon-networking-025d543-pickup-object-sync.png)

VRCPickup ajoute un Rigidbody à votre GameObject s'il n'en a pas déjà un, et signale à VRChat qu'il autorise l'objet à être ramassé et transfère la propriété de l'objet à celui qui le saisit.

VRCObjectSync synchronise automatiquement l'objet en envoyant sa position, sa rotation, son échelle et certaines propriétés physiques aux autres joueurs afin qu'il soit identique pour tout le monde. Pour synchroniser d'autres données, vous avez besoin de variables.

# Variables
Une variable est un conteneur pour une valeur. Les UdonBehaviours exécutent des programmes Udon, et vous pouvez y ajouter des variables.
![La fenêtre des variables dans un graphique Udon affiche les variables que vous avez créées et vous permet de modifier leurs propriétés.](/img/worlds/index-e057e35-slider-program-variables.png)
Dans l'image ci-dessus, j'ai créé trois variables différentes, et vous pouvez voir que j'ai coché la case "synced" pour la variable "sliderValue". Le propriétaire de ce GameObject est responsable de la valeur de cette variable, et ses modifications seront envoyées à tous les autres.

## Exemple : Slider synchronisé
![](/img/worlds/udon-networking-8472b6b-synced-slider.png)

Dans cet exemple, le propriétaire d'un Slider synchronise sa valeur avec tous les autres. Notez que cela est destiné à illustrer les concepts - nous publierons un exemple séparé qui explique les détails pratiques.

Pour synchroniser le Slider, nous avons simplement besoin de récupérer sa valeur numérique. Il s'agira d'un nombre avec une virgule entre 0 et 1, que nous appelons une valeur à virgule flottante, ou float en abrégé. Nous créons donc une variable appelée *sliderValue*, de type **float**.

Nous configurons notre Slider pour mettre à jour cette valeur chaque fois que le Slider est déplacé. Pour le propriétaire, c'est simple : lorsque le Slider se déplace, nous obtenons sa nouvelle valeur et mettons à jour notre variable. Cette valeur sera emballée et envoyée à tous les autres, ce qui s'appelle la sérialisation. Lorsqu'elle est reçue et déballée par les autres utilisateurs, cela s'appelle la désérialisation.

Ainsi, le propriétaire déplace le Slider et définit *sliderValue*. VRChat met à jour *sliderValue* sur les autres joueurs et déclenche un événement appelé **OnDeserialization** chez les autres utilisateurs. Lorsque cet événement est déclenché, ils utilisent *sliderValue* pour mettre à jour la position du Slider et le texte dans l'affichage.

Propriétaire : Déplace le Slider > OnValueChanged > définit *sliderValue* à partir de **UISlider.value** > Mettre à jour l'affichage.
Autres : *sliderValue* mis à jour par VR

Chat > OnDeserialization déclenché > définit **UISlider.value** > OnValueChanged > Mettre à jour l'affichage.

# Événements
Les événements se produisent, puis disparaissent. Contrairement aux variables, qui ne peuvent être mises à jour que par le propriétaire d'un objet, n'importe qui peut appeler un événement sur un objet. Vous pouvez choisir de l'envoyer à tout le monde ou seulement au propriétaire de cet objet. Cela se fait en sélectionnant la cible : Tous (All) ou la cible : Propriétaire (Owner) lors de l'envoi de l'événement.
![](/img/worlds/udon-networking-c764485-scne.png)

## Exemple : Pistolet à bulles
![](/img/worlds/udon-networking-33702b1-bubble-gun-shooting.png)

Dans cet exemple, nous avons un objet avec un système de particules et un animateur qui fait tourner sa baguette à bulles et génère des particules de bulles. Nous voulons que cela se produise pour tout le monde dans le monde lorsque l'utilisateur tenant la baguette appuie sur la gâchette.

Dans notre graphe Udon, nous avons un événement personnalisé que nous appelons "Trigger" qui lance l'animation 'Spin' et déclenche l'émission de 22 particules - il s'agit simplement d'un événement local dans notre graphe.

Pour que cela se produise pour tout le monde, nous associons l'événement **OnPickupUseDown** qui est déclenché lorsque quelqu'un appuie sur "Utiliser" tout en tenant notre pistolet à bulles, et nous utilisons **SendCustomNetworkEvent** avec une cible (target) "Tous" pour déclencher l'événement "Trigger" pour tout le monde, y compris le propriétaire de l'objet.
![](/img/worlds/udon-networking-e21b3b0-bubble-gun-graph.png)

# Concept supplémentaire : Arrivée tardive
Que se passe-t-il pour les personnes qui rejoignent votre monde après qu'une synchronisation ait eu lieu ? C'est simple : les variables seront mises à jour, les événements non. Lorsque quelqu'un rejoint votre monde, l'événement OnDeserialization sera déclenché pour chaque objet en réseau du monde avec les dernières données, et ils exécuteront la logique que vous avez mise en place pour mettre à jour les choses en fonction de ces données. Les événements ont disparu, cependant - il n'y a aucune raison de déclencher les particules de bulles une heure après que quelqu'un a appuyé sur la gâchette.

# Récapitulatif de l'aperçu
La synchronisation se fait via les variables et les événements. Pour les variables, le propriétaire d'un objet en réseau met à jour une variable et envoie ces données à tous les autres joueurs qui les désérialisent. Toute personne entrant dans un monde obtient les dernières données à désérialiser. Pour les événements, n'importe qui peut envoyer un événement réseau. Il sera soit reçu par le propriétaire, soit par tout le monde dans le monde à ce moment-là.

# Package d'exemple
[UdonNetworkingConcepts.unitypackage](https://assets.vrchat.com/sdk/UdonNetworkingConcepts.unitypackage)

Nous avons inclus les trois exemples ci-dessus dans un package simple que vous pouvez importer dans n'importe quel projet qui dispose du SDK Udon afin de les voir fonctionner et d'explorer les graphiques vous-même.
:::note Plus de détails

Cette première section sert de présentation générale de la mise en réseau avec Udon dans VRChat. Une fois que vous pensez avoir compris les concepts et que vous avez exploré le package d'exemple ci-dessus, vous pouvez en apprendre davantage sur chaque aspect du système en consultant les détails ci-dessous.
:::

# Les moyens de synchronisation
Il existe quatre façons de synchroniser les données et les événements dans votre monde :

### 1. Variable continue
Utilisez cette méthode lorsque vous avez une variable que vous souhaitez mettre à jour fréquemment, et il est acceptable qu'elle ne soit parfois pas mise à jour pour économiser la bande passante pour d'autres choses. Cela se synchronisera pour les arrivées tardives.

**Exemple** : Un arbre qui grandit lorsque quelqu'un l'arrose, avec une variable "taille" continue. Il est acceptable de manquer quelques mises à jour car il se déplacera à la bonne position lors de la prochaine mise à jour que vous recevrez. Voir [Utilisation des variables](/worlds/udon/networking#utilisation-des-variables) ci-dessous.

### 2. Variable manuelle
Utilisez cette méthode lorsque vous avez une variable qui sera mise à jour moins fréquemment et qu'il est extrêmement important que sa valeur soit toujours à jour. Cela se synchronisera pour les arrivées tardives. Cette option n'est pas compatible avec Object Sync. Voir [Utilisation des variables](/worlds/udon/networking#utilisation-des-variables) ci-dessous.

**Exemple** : Le "score" de chaque équipe dans un match de basketball. Cela change uniquement lorsque quelqu'un marque un panier et vous ne voulez certainement pas manquer une mise à jour.

### 3. Événements personnalisés
Utilisez ceci pour déclencher un événement pour chaque joueur actuellement dans l'instance, ou pour le propriétaire d'un objet. Il est garanti que l'événement arrivera, mais il y aura un certain délai et des frais généraux. Il ne sera pas reçu par les personnes qui se joignent après l'envoi de l'événement. Voir [Utilisation des événements](/worlds/udon/networking#utilisation-des-événements) ci-dessous.

**Exemple** : Un effet laser qui se déclenche dans votre Club de danse. Vous voulez que tout le monde dans le club le voie à peu près en même temps, mais s'il arrive 20 minutes plus tard, ce n'est pas grave s'il l'a manqué.

### 4. Automatique
Certains objets spécifiques à VRChat sont automatiquement synchronisés. Cela inclut :
* Avatars : comprend leurs colliders, leur voix et leur mouvement IK.
* VRCObjectSync : comprend la transformation et le rigidbody de l'objet.

# Propriété d'objet
Dans VRChat, chaque GameObject est "possédé" par un joueur

(VRCPlayerApi) à la fois. Seul le propriétaire d'un objet peut modifier ses variables Udon synchronisées. Ces modifications peuvent ensuite être envoyées à tous les autres joueurs présents dans l'instance. Si vous souhaitez qu'un joueur puisse modifier une variable sur un objet, assurez-vous de vérifier ou de demander la propriété en premier !

La propriété d'un objet peut être modifiée avec Udon en appelant `Networking.SetOwner(VRCPlayerApi player, GameObject obj)`. Cela fera en sorte que chaque joueur dans l'instance appelle `OnOwnershipTransferred(VRCPlayerApi player)`, où `player` est une référence au nouveau propriétaire de l'objet. Le nouveau propriétaire peut immédiatement modifier les variables synchronisées. Si votre script utilise une synchronisation manuelle, n'oubliez pas d'appeler `RequestSerialization()`.

## Demande de propriété (Avancé)

Si vous souhaitez que le propriétaire d'un objet puisse accepter ou refuser les transferts de propriété, ajoutez l'événement `OnOwnershipRequest(VRCPlayerApi requester, VRCPlayerApi newOwner)` à votre script.

En ajoutant `OnOwnershipRequest()` à votre script, des étapes supplémentaires sont effectuées lors d'un transfert de propriété :

1. Comme précédemment, le **joueur demandeur** doit appeler `Networking.SetOwner(VRCPlayerApi player, GameObject obj)` pour commencer le transfert de propriété.
   - Le joueur "demandeur" peut être n'importe quel joueur ou le propriétaire. Si un ancien propriétaire a effectué la demande, il saute les étapes 4 et 5.
   - Les propriétaires peuvent donner la propriété à n'importe qui, mais les non-propriétaires ne peuvent demander la propriété que pour eux-mêmes. (Les scripts sans `OnOwnershipRequest()` n'ont pas cette restriction.)
2. `OnOwnershipRequest(VRCPlayerApi requester, VRCPlayerApi newOwner)` est appelé par le **joueur demandeur**.
   - Le joueur demandeur doit renvoyer `true` pour approuver la demande. Sinon, la demande est annulée rapidement.
3. `OnOwnershipTransferred(VRCPlayerApi player)` est appelé par le **joueur demandeur**.
   - Cela se produit *avant* que la propriété ne soit confirmée par le propriétaire. La propriété peut revenir à l'ancien propriétaire si le transfert est refusé.
4. `OnOwnershipRequest(VRCPlayerApi requester, VRCPlayerApi newOwner)` est appelé par le **propriétaire**.
   - Si le propriétaire renvoie `true`, le transfert de propriété est accepté. (Dans le graphe Udon, `SetReturnValue` est utilisé pour renvoyer `true`.)
   - Si le propriétaire renvoie `false` ou ne renvoie pas de valeur du tout, le transfert de propriété est refusé. `OnOwnershipTransferred()` est appelé pour le joueur demandeur, l'informant que l'ancien propriétaire possède toujours l'objet.
   - Cette étape est ignorée si le propriétaire transfère la propriété à quelqu'un. Le nouveau joueur ne peut pas refuser la propriété.
5. Si la demande est acceptée, `OnOwnershipTransferred(VRCPlayerApi player)` est appelé par l'**ancien propriétaire** et **tous les autres joueurs**.

# Utilisation des variables

:::note L'utilisation d'une variable pour synchroniser des données nécessite trois étapes :

1. Créer la variable.
2. Mettre à jour la valeur sur le propriétaire.
3. Réagir aux changements de valeur reçus du propriétaire.
:::
### Créer la variable
1. Cliquez sur le bouton + dans la fenêtre des variables.
2. Choisissez le type de variable.
3. Renommez votre variable (facultatif, mais faites-le).
4. Cliquez sur la flèche à côté du nom de la variable pour afficher plus d'options, activez "synced" (synchronisé). (La valeur par défaut "none" est correcte - cela signifie simplement que la valeur n'est pas automatiquement lissée.)

### Mettre à jour la valeur sur le propriétaire
1. Faites glisser la variable sur votre graphe tout en maintenant la touche "Ctrl" enfoncée pour créer un nœud "Set Variable".
2. Connectez un événement ou un flux au port de flux (Flow Port) de ce nœud, et connectez une nouvelle valeur au port de valeur (Value Port).
3. Si ce UdonBehaviour utilise une synchronisation continue (sélectionnée sur le UdonBehaviour lui-même dans l'inspecteur), vous avez terminé la mise à jour de la valeur. Si vous utilisez une synchronisation manuelle, vous devez ajouter un nœud "UdonBehaviour.RequestSerialization" et connecter la sortie de votre port de flux (Flow Port) "Set Variable" à l'entrée de flux (Flow Input port) de ce nœud. Vous pouvez laisser le port de valeur (Value Port) 'instance' de ce nœud vide, il sera par défaut au UdonBehaviour actuel, ce que nous voulons.

### Réagir aux changements de valeur reçus du propriétaire
1. Ajoutez un nœud "OnDeserialization" à ce même graphe.
2. Faites glisser et déposez la variable sur votre graphe sans maintenir la touche Ctrl enfoncée pour créer un nœud "Get Variable".
3. Utilisez le flux provenant du nœud OnDeserialization et la valeur provenant du nœud Get Variable pour mettre à jour un autre nœud avec cette nouvelle valeur.

## RequestSerialization
Ce nœud est utilisé en mode synchronisation manuelle pour marquer les variables du UdonBehaviour cible en vue de la sérialisation lors de la prochaine itération du réseau, qui ne se produit pas à chaque image. Ce nœud fonctionne bien avec le nœud d'événement OnPreSerialization. Vous déclenchez "RequestSerialization" et ensuite l'événement OnPreSerialization sera déclenché lors de la prochaine itération du réseau. À ce moment-là, vous pouvez mettre à jour les variables avec les valeurs que vous souhaitez synchroniser.
:::note Synchronisation des variables

Vous pouvez synchroniser des variables et des tableaux de variables des types suivants : bool, char, byte, sbyte, short, ushort, int, uint, long, ulong, float, double, Vector2, Vector3, Vector4, Quaternion, string, VRCUrl, Color et Color32.
:::

:::caution

Lors de la synchronisation de variables, assurez-vous de prendre en compte les performances et la bande passante. Les mises à jour fréquentes de variables peuvent entraîner une utilisation excessive de la bande passante, en particulier dans les instances comportant de nombreux joueurs. Si possible, limitez les mises à jour fréquentes aux valeurs qui ont un impact significatif sur l'expérience du joueur.

De plus, n'oubliez pas que les variables synchronisées ne sont pas immédiatement mises à jour sur les clients. Il peut y avoir un certain délai entre la modification de la variable par le propriétaire et la réception de la mise à jour par les autres joueurs. Tenez compte de ce délai lors de la conception de votre expérience multijoueur.

Enfin, veillez à utiliser les types de variables appropriés pour les données que vous souhaitez synchroniser. Par exemple, utilisez un type entier pour les compteurs ou les identifiants uniques, et utilisez un type de vecteur pour les positions ou les orientations dans l'espace 3D.

# Utilisation des événements

Les événements sont utilisés pour déclencher une action ou une réaction spécifique dans votre monde VRChat. Ils peuvent être déclenchés par n'importe quel joueur et peuvent être envoyés à tous les autres joueurs ou uniquement au propriétaire de l'objet.

Voici comment utiliser les événements dans Udon :

### Créer un événement personnalisé
1. Cliquez sur le bouton + dans la fenêtre des événements.
2. Renommez votre événement (facultatif, mais faites-le).
3. Sélectionnez la cible de l'événement : Tous (All) ou Propriétaire (Owner). Si vous choisissez Propriétaire, seuls les joueurs qui possèdent l'objet recevront l'événement.
4. Si vous le souhaitez, vous pouvez définir une étiquette (label) pour l'événement, ce qui peut être utile pour organiser et filtrer les événements dans des graphes plus complexes.

### Déclencher un événement
Pour déclencher un événement dans votre graphe Udon, vous pouvez utiliser le nœud "SendCustomNetworkEvent" :

1. Faites glisser et déposez le nœud "SendCustomNetworkEvent" sur votre graphe.
2. Connectez un événement ou un flux à l'entrée "Send" de ce nœud.
3. Sélectionnez l'événement que vous souhaitez déclencher dans le menu déroulant de l'entrée "Event Name".
4. Sélectionnez la cible de l'événement : Tous (All) ou Propriétaire (Owner).
5. Si vous souhaitez ajouter des données supplémentaires à l'événement, vous pouvez le faire en connectant des flux de données aux entrées "Data" du nœud "SendCustomNetworkEvent". Vous pouvez utiliser des variables ou d'autres sources de données pour fournir ces valeurs.

### Réagir à un événement reçu
Pour réagir à un événement reçu dans votre graphe Udon, vous pouvez utiliser le nœud "OnCustomNetworkEvent" :

1. Faites glisser et déposez le nœud "OnCustomNetworkEvent" sur votre graphe.
2. Sélectionnez l'événement auquel vous souhaitez réagir dans le menu déroulant de l'entrée "Event Name".
3. Connectez les actions ou les nœuds que vous souhaitez déclencher en réponse à l'événement à la sortie "Received" du nœud "OnCustomNetworkEvent".
4. Vous pouvez également accéder aux données supplémentaires envoyées avec l'événement en utilisant les sorties "Data" du nœud "OnCustomNetworkEvent". Ces sorties fournissent les valeurs des données sous forme de variables que vous pouvez utiliser dans votre graphe.

:::caution Considérations pour les événements

Lors de l'utilisation d'événements, il est important de tenir compte des performances et de la bande passante. Les événements sont envoyés à tous les joueurs de l'instance, ce qui peut entraîner une utilisation excessive de la bande passante si vous en envoyez fréquemment ou avec beaucoup de données supplémentaires. Assurez-vous de limiter les événements aux actions et aux réactions essentielles pour l'expérience du joueur.

De plus, n'oubliez pas que les événements ne sont pas immédiatement reçus par les clients. Il peut y avoir un certain délai entre l'envoi de l'événement par le joueur et sa réception par les autres joueurs. Tenez compte de ce délai lors de la conception de votre expérience multijoueur.

Enfin, soyez conscient de la sécurité lors de l'utilisation d'événements. Les événements peuvent être déclenchés par n'importe quel joueur, il est donc important de mettre en place des mesures de sécurité pour éviter les abus ou les utilisations malveillantes des événements.