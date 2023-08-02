

# Aperçu
Lorsque vous créez des programmes dans le graphique, vous utilisez principalement des Nœuds. Il existe quelques autres éléments disponibles, décrits ici.

# Groupes
Les groupes sont utiles pour organiser et décrire votre graphique. Ils ne *modifient pas* la façon dont vos graphiques fonctionnent ou sont compilés.
![Vous pouvez sélectionner des éléments et faire un clic droit pour obtenir la fonction *Créer un groupe*.] (/img/worlds/graph-elements-e9a0713-create-group.gif)
Pour créer des groupes, vous pouvez :
* Faites un clic droit dans le graphique et choisissez "Créer un groupe", puis faites glisser et déposer les éléments dans le groupe.
* Sélectionnez des éléments avec un glisser-déposer en boîte ou en maintenant la touche Ctrl enfoncée pendant que vous cliquez dessus, puis faites un clic droit sur le graphique et choisissez "Créer un groupe", ou appuyez sur "Ctrl+G" pour un regroupement rapide.

Pour supprimer des éléments des groupes, vous pouvez :
* Sélectionnez les éléments, maintenez la touche Maj enfoncée, puis faites glisser les éléments hors du groupe.
* Sélectionnez les éléments, faites un clic droit et choisissez "Supprimer du groupe".

Pour accéder à un groupe dans le graphique, cliquez dessus dans la barre latérale du graphique.
:::note Groupes imbriqués

Actuellement, les groupes imbriqués ne sont pas pris en charge. Le comportement actuel de regroupement est de supprimer le groupe existant si vous essayez de le sélectionner et de l'entourer avec un nouveau groupe.
:::
# Commentaires

Les commentaires sont de simples blocs de texte que vous pouvez placer à côté des éléments nécessitant plus d'informations.
![Un commentaire à côté d'un nœud.] (/img/worlds/graph-elements-80881a1-simple-comment.png)
Vous pouvez créer des commentaires en faisant un clic droit sur le graphique et en choisissant *Créer un commentaire*. Vous pouvez également les ajouter à des groupes. Vous pouvez utiliser des commentaires et des groupes ensemble pour une lisibilité optimale !
![Le graphique 'SendEventOnTimer' inclus dans le dossier Exemples de VRChat utilise des groupes et des commentaires pour expliquer ce qui se passe dans le graphique.] (/img/worlds/graph-elements-ab506db-comments-and-groups.png)

# Nœuds
Les nœuds d'un graphique sont ce qui connecte tout ensemble, et c'est ainsi qu'Udon tire son nom ! Ils relient les nœuds ensemble via leurs ports. Ils sont colorés en fonction des ports auxquels ils sont connectés, donc si vous connectez deux ports avec des types différents, vous verrez le changement de couleur à mi-chemin. Dans la documentation Unity et ailleurs, on les appelle "arêtes" - donc si vous voyez une référence aux arêtes, il s'agit de nos délicieux fils.