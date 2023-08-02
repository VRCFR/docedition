

# Recherche rapide

Appuyez sur la touche **Espace** pour ouvrir la Recherche rapide, puis tapez les premières lettres de la classe avec laquelle vous souhaitez interagir.
![](/img/worlds/searching-for-nodes-b2c9ea7-gameobject-search.png)

# Recherche complète

Appuyez sur **Tab** pour ouvrir la Recherche complète, puis vous pouvez rechercher n'importe quelle méthode sur n'importe quel objet. Par exemple, pour GameObject.GetName, vous pouvez simplement chercher 'getname' et voir tous les objets ayant une méthode pour obtenir le nom de l'objet. Vous pouvez également rechercher directement 'gameobject.getname' et vous serez dirigé vers le nœud correspondant. Cette méthode de recherche est plus lente que la Recherche rapide, elle doit donc être utilisée seulement lorsque vous n'êtes pas sûr(e) de la classe à rechercher dans la Recherche rapide.
![image](/img/worlds/searching-for-nodes-0f8fb2b-fullsearch.png)

# Barre de recherche

Il y a une barre de recherche en haut de la barre latérale du graphique Udon qui vous permet de rechercher dans votre graphique. 
Vous pouvez utiliser "Ctrl+F" pour la mettre en surbrillance depuis la fenêtre du graphique.
La recherche commencera à afficher des résultats après avoir saisi plus de 3 caractères.
Appuyer sur "Entrée" lorsque des résultats de recherche sont affichés permet de passer d'un résultat à l'autre, dans l'ordre de "la meilleure correspondance d'abord".
![](/img/worlds/searching-for-nodes-4647159-search.png)

# Recherche ciblée

Ce mode est désactivé par défaut, donc vous devez d'abord accéder à votre écran d'accueil en cliquant sur 'Accueil' dans le coin supérieur gauche d'un graphique. Ensuite, cochez la case à côté de 'Recherche ciblée sur le nœud sélectionné'. Cela vous permet de passer rapidement à la deuxième partie de la Recherche rapide - si vous avez un nœud GameObject.GetName, vous pouvez le sélectionner et appuyer sur **Espace** pour ouvrir une recherche de plus de méthodes de **GameObject** .
![Recherche sur des classes particulières en appuyant sur **Espace** avec un nœud sélectionné](/img/worlds/searching-for-nodes-3ef349a-focused-search.png)

# Recherche lors du lâcher de nœud

Ce mode est également désactivé par défaut - vous devrez ouvrir votre écran d'accueil et cocher la case à côté de 'Recherche lors du lâcher de nœud'. Une fois activé, vous pouvez faire glisser un fil d'un port et le lâcher dans un espace vide pour ouvrir une recherche de **n'importe quel** nœud pouvant se connecter à ce port. Cela fonctionne dans les deux sens et recherchera également des variables pouvant être connectées.
![image](/img/worlds/searching-for-nodes-8656333-portsearch.gif)