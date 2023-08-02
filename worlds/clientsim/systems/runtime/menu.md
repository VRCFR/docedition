

# Client Sim Menu

Le ClientSimMenu a quatre pages qui peuvent être affichées en fonction de la situation. Le menu est désormais positionné dans l'espace monde au lieu d'être une superposition sur la caméra. Il sera rendu par-dessus tout pour garantir aux joueurs la possibilité d'utiliser le menu.

## Page d'avertissement

![Avertissement](/images/warning.png)

La page d'avertissement s'affiche à chaque fois que ClientSim démarre. Cette page informe l'utilisateur que ClientSim n'est pas identique à VRChat et qu'il y aura des différences. Elle ne contient qu'un seul bouton, que l'utilisateur doit appuyer pour fermer la page et le menu.

## Page de pause

![Pause](/images/pause.png)

La page de pause s'affiche lorsque l'utilisateur ouvre le menu après avoir accepté la page d'avertissement. Cette page comporte trois sections : Actions, Infos sur le joueur et Paramètres.

## Actions

La section Actions contient quatre boutons :
1. Fermer le menu - Ferme le menu et permet le déplacement du joueur
2. Retrouver - Ferme le menu et téléporte le joueur au point d'apparition
3. Fenêtre des paramètres - Ouvre la [fenêtre des paramètres](../editor/settings-window.md) de ClientSim
4. Quitter le mode lecture - Quitte le mode lecture et retourne au mode édition

## Infos sur le joueur

La section Infos sur le joueur contient des informations concernant le joueur local.
1. Nom du joueur
2. ID du joueur
3. Le joueur local est-il le maître ?
4. Le joueur local est-il le propriétaire de l'instance ?
5. Un bouton pour faire apparaître des joueurs distants à des fins de test

## Paramètres

La section Paramètres offre des options pour modifier les paramètres actuels de ClientSim. Les modifications de ces paramètres seront enregistrées même après la fin du mode lecture.
* **Afficher les info-bulles** - Active ou désactive l'affichage des info-bulles d'interaction.
* **Réticule sur le bureau** - Active ou désactive le réticule sur le bureau, au centre de l'écran. Cela ne désactive pas le pointeur de l'interface utilisateur si celui-ci survole un objet interactif.
* **Inverser le mouvement de la souris** - Active ou désactive l'inversion de l'axe Y de la souris.
* **Journal de la console** - Active ou désactive l'enregistrement des informations de débogage dans la console.
* **Hauteur du joueur** - Un curseur pour définir la hauteur du joueur. La valeur par défaut est de 1,9 unités Unity. La plage du curseur est comprise entre 0,2 et 4 unités. Si la valeur dans la fenêtre des paramètres de ClientSim Unity est définie, alors la hauteur peut être outrepassée jusqu'à 80 unités. L'ouverture du menu limitera la valeur maximale pour maintenir la plage du curseur utilisable sans quitter le mode lecture. Notez que la hauteur du joueur est différente de l'échelle de suivi, bien que les valeurs soient liées.

## Page de démarrage retardé

![Délai](/images/delay.png)

La page de démarrage retardé s'affiche chaque fois que les [paramètres de ClientSim](settings.md) prévoient une valeur non nulle pour le temps de retard de démarrage de ClientSim. Cette page se fermera automatiquement lorsque ClientSim démarre. Si le contrôleur du joueur a été généré, la page d'avertissement s'affichera alors. L'utilisateur ne peut pas fermer cette page et doit attendre la durée spécifiée ou quitter le mode lecture.

## Page de paramètres non valides

![Paramètres non valides](/images/invalid-settings.png)

La page de paramètres non valides s'affiche lorsque l'utilisateur a des paramètres du projet Unity qui ne sont pas configurés pour utiliser ClientSim. Cela peut se produire juste après l'importation de ClientSim ou si l'utilisateur modifie un paramètre sur lequel ClientSim repose. Lorsqu'elle est affichée, la [fenêtre des paramètres](../editor/settings-window.md) est forcée d'apparaître afin que les utilisateurs puissent cliquer sur les boutons nécessaires pour modifier les paramètres du projet. Si le joueur n'a pas les paramètres Unity d'entrée corrects, les boutons du menu ne produiront aucun effet. Il n'y a aucun moyen de contourner cette page, à part quitter le mode lecture et corriger les paramètres non valides.