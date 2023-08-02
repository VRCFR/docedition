

Vous pouvez lire l'entrée du contrôleur d'un joueur de manière unifiée sur toutes les plateformes en utilisant les événements d'entrée Udon. Ces événements fonctionneront correctement même lorsque le joueur a remappé ses contrôles.

Il existe actuellement deux types d'événements - Bouton et Axe, qui incluent des valeurs booléennes et des valeurs décimales. Chaque événement contient également un objet spécial [UdonInputEventArgs ](/mondes/udon/evenements-dentree#UdonInputEventArgs).

# Événements de bouton

Les événements de bouton incluent une valeur booléenne qui est **true** lorsque le bouton est enfoncé et **false** lorsqu'il est relâché.

### InputJump
Barre d'espace sur ordinateur de bureau, généralement un bouton de face sur les contrôleurs.

### InputUse
Clic gauche sur ordinateur de bureau, généralement un bouton de déclenchement sur les contrôleurs.

### InputGrab
Clic gauche sur ordinateur de bureau, généralement un bouton de préhension sur les contrôleurs de réalité virtuelle.

### InputDrop
Clic droit sur ordinateur de bureau, appuyer sur le bouton de préhension sur les contrôleurs Vive Wands et certains contrôleurs de réalité mixte Windows, relâcher le bouton de préhension sur les autres.

# Événements d'axe

Les événements d'axe ont une valeur décimale qui varie généralement entre -1 et 1. Lorsque vous utilisez un contrôleur avec des sticks analogiques, un nouvel événement sera déclenché pour chaque changement de valeur, de 0 à 0.1, puis à 0.2, etc. Les utilisateurs d'ordinateur de bureau afficheront des nombres entiers : -1, 0, 1, etc.

### InputMoveHorizontal
A et D sur ordinateur de bureau, généralement le stick/gauche déplaçant le curseur de gauche à droite sur les contrôleurs.

### InputMoveVertical
W et S sur ordinateur de bureau, généralement le stick/gauche déplaçant le curseur de haut en bas sur les contrôleurs.

### InputLookVertical
Déplacement de la souris de haut en bas sur ordinateur de bureau, généralement le stick droit vers le haut et vers le bas sur les manettes de jeu et les contrôleurs de réalité virtuelle.

### InputLookHorizontal
Déplacement de la souris de gauche à droite sur ordinateur de bureau, rotation vers la gauche et vers la droite à l'aide du stick/gauche sans rotation confort sur les contrôleurs de réalité virtuelle, généralement le stick droit de gauche à droite sur les manettes de jeu.

# UdonInputEventArgs

Cet objet est inclus dans chaque événement d'entrée et contient des données supplémentaires pour l'événement qui peuvent être utiles. Nous pourrions ajouter plus de données dans cet objet à l'avenir, faites-nous savoir si vous pensez à quelque chose de pratique que vous aimeriez référencer ici. Pour l'instant, il inclut :

**UdonInputEventType**: BOUTON ou AXE
**boolValue**: Vrai/Faux s'il s'agit d'un événement de bouton, faux s'il s'agit d'un événement d'axe (valeur par défaut)
**floatValue**: Nombre entre -1 et 1 pour un événement d'axe, 0 s'il s'agit d'un événement de bouton (valeur par défaut)
**handType**: GAUCHE ou DROITE. Inclus pour les utilisateurs de clavier et de souris également (la souris est DROITE, le clavier est GAUCHE).