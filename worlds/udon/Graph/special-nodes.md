

Ce sont des nœuds "spéciaux". Cela inclut le contrôle de flux et les fonctionnalités spéciales d'Udon.

### Bloc
Divise le flux en plusieurs sections. Une entrée de flux, plusieurs sorties de flux. Exécute tous les emplacements de flux de droite de haut en bas.

### Branche
Entrées : `Bool` - `System.Boolean`
Effectue une branche d'exécution basée sur une évaluation conditionnelle. Si `Bool` est vrai, le chemin de flux "Vrai" est exécuté. Si `Bool` est faux, le chemin de flux "Faux" est exécuté.

### Commentaire
Fournit un espace pour que l'utilisateur saisisse une chaîne de commentaire. Cette chaîne n'est pas incluse lors de la compilation.

### Const Null
Fournit une valeur "null" à des fins de vérification de nullité.

### Const This
Fournit une référence à l'objet GameObject dont le comportement d'Udon est un composant.

### Événement personnalisé
Entrées: `name` - `System.String`
Reçoit un événement personnalisé. Le nom de l'événement personnalisé doit être saisi, il ne peut pas être fourni via l'entrée du nœud.

### Pour
Entrées : `start`, `end`, `step` - `System.Int32`
Sorties : `index` - `System.Int32`
Exécute le flux en utilisant un compteur. Un compteur est initialisé avec la valeur de `start`. Le flux `Body` est exécuté, puis le compteur est incrémenté par la valeur de `step`. Cela se poursuit jusqu'à ce que la valeur du compteur soit supérieure à `end`. Une fois cela effectué, le flux continue sur le flux `Exit`.

### Obtenir Variable
Entrées : `name` - `System.String`
Sorties : `System.Object`
Obtient la variable Udon nommée `name` et la fournit en sortie.

### Définir Variable
Entrées : `name` - `System.String` `value` - `System.Object` `sendChange` - `Boolean`
Définit la variable Udon nommée `name` sur la valeur `value` lors de l'exécution du flux. Si `sendChange` est cochée, cela déclenchera également l'événement OnVariableChanged pour cette variable.

### Obtenir Variable de Programme
Entrées : `instance` - `UdonBehaviour` `symbolName` - `string`
Obtient la valeur d'une variable Udon `symbolName` à partir d'un autre `instance` de UdonBehaviour. Cela fonctionne mieux si le UdonBehaviour cible est une variable publique et qu'elle est connectée dans l'Inspecteur, ce qui vous permet de choisir le nom de la variable cible dans un menu déroulant. Si aucun UdonBehaviour n'est connecté à l'instance, il utilisera les noms de variables du UdonBehaviour actuel. Si vous connaissez plutôt le nom de la variable et que vous voulez le définir directement, utilisez un nœud `String const` pour l'écrire à la main.

### Définir Variable de Programme
Entrées : `instance` - `UdonBehaviour` `symbolName` - `string` `value` - `Object`
Définit la valeur d'une variable Udon `symbolName` sur un autre `instance` de UdonBehaviour à `value`. Cela fonctionne mieux si le UdonBehaviour cible est une variable publique et qu'elle est connectée dans l'Inspecteur, ce qui vous permet de choisir le nom de la variable cible dans un menu déroulant. Si aucun UdonBehaviour n'est connecté à l'instance, il utilisera les noms de variables du UdonBehaviour actuel. Si vous connaissez plutôt le nom de la variable et que vous voulez le définir directement, utilisez un nœud `String const` pour l'écrire à la main. Ce nœud déclenchera également l'événement OnVariableChanged pour la variable cible.

### Sur le Changement de Variable
Sorties : `newValue` `oldValue`
Se déclenche chaque fois que SetProgramVariable est appelé sur la variable cible, ou lorsque Set Variable est appelée avec `sendChange` cochée. Fonctionne également pour les variables synchronisées !

### Tant que
Entrées : `Bool` - `System.Boolean`
Exécute le flux de `Body` tant que `Bool` est vrai. Si `Bool` est faux, exécute le flux `Exit`.

## Nœuds UdonBehaviour
Les UdonBehaviours ont quelques nœuds spéciaux :

### Envoyer un événement personnalisé
Entrées : `instance` - `UdonBehaviour`, `eventName` - String
Exécute l'événement "eventName" sur le UdonBehaviour cible. Si l'instance est laissée vide, elle pointe vers l'un de ses propres événements.

### Envoyer un événement personnalisé avec un délai de frames
Entrées : `instance` - `UdonBehaviour`, `eventName` - String, `delayFrames` - int, `eventTiming` - EventTiming
Exécute l'événement "eventName" sur le UdonBehaviour cible après avoir attendu `delayFrames`. L'événement sera exécuté pendant la mise à jour (Update) ou la mise à jour tardive (LateUpdate), en fonction de l'option `eventTiming` sélectionnée. Le délai minimal est de 1 frame.

### Envoyer un événement personnalisé avec un délai de secondes
Entrées : `instance` - `UdonBehaviour`, `eventName` - String, `delaySeconds` - float, `eventTiming` - EventTiming
Exécute l'événement "eventName" sur le UdonBehaviour cible après avoir attendu `delaySeconds`. L'événement sera exécuté pendant la mise à jour (Update) ou la mise à jour tardive (LateUpdate), en fonction de l'option `eventTiming` sélectionnée.

### Envoyer un événement réseau personnalisé
Entrées : `instance` - `UdonBehaviour`, `target` - NetworkEventTarget, `eventName` - String
Exécute l'événement "eventName" sur le UdonBehaviour cible - soit sur le propriétaire de la cible si 'Owner' est sélectionné comme cible, soit sur tout le monde dans l'instance si 'all' est sélectionné.