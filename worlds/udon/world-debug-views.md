

Voici les outils que vous pouvez utiliser pour déboguer vos mondes en jeu.

Pour accéder aux vues de débogage, vous avez besoin de deux choses :
* Lancez VRChat avec le paramètre de lancement `--enable-debug-gui`
* Appuyez sur Rshift + Tilde + 1-9.

Si vous avez un clavier où le tilde n'est pas directement à gauche de la touche 1, essayez d'utiliser la touche directement à gauche de la touche 1, car elle priorisera la position de la touche plutôt que le caractère lui-même.
![world-debug-views-2103941-szhLVX11II.png](/img/worlds/world-debug-views-2103941-szhLVX11II.png)

# Menu de débogage 1

![world-debug-views-9bfe518-VRChat_Q9pMRjUJHI.png](/img/worlds/world-debug-views-9bfe518-VRChat_Q9pMRjUJHI.png)

Le menu de débogage 1 affiche des informations sur votre connexion à l'API de VRChat. Il est principalement sans importance pour le développement de mondes.
# Menu de débogage 2

![world-debug-views-ae12b10-VRChat_kGTo5o998Y.png](/img/worlds/world-debug-views-ae12b10-VRChat_kGTo5o998Y.png)

Le menu de débogage 2 affiche la version actuelle de VRChat que vous utilisez, ainsi que vos FPS.
# Menu de débogage 3

![world-debug-views-e85c111-VRChat_gk2BOiYkIr.png](/img/worlds/world-debug-views-e85c111-VRChat_gk2BOiYkIr.png)

Le menu de débogage 3 affiche votre journal de sortie. Le journal de sortie est très utile pour les créateurs de mondes car il peut vous montrer des informations telles que les plantages de comportement Udon, toutes les informations enregistrées via les nœuds Debug.Log, et toute autre erreur potentielle dans votre monde générée par Unity ou VRChat.

Vous pouvez maintenir la touche Tab enfoncée pour activer le curseur de la souris et utiliser les boutons en haut pour activer et désactiver différentes options, ainsi que faire défiler la sortie du journal.
# Menu de débogage 4

![world-debug-views-0db830e-VRChat_pZdYm9u4ox.png](/img/worlds/world-debug-views-0db830e-VRChat_pZdYm9u4ox.png)

Le menu de débogage 4 affiche diverses statistiques sur les autres utilisateurs.
* M : Indique si l'utilisateur est le maître de l'instance (c'est-à-dire la personne ayant été dans l'instance depuis le plus longtemps)
* L : Indique si l'utilisateur est le joueur local
* VR : Indique si l'utilisateur est en VR
* Ping : Le ping de l'utilisateur
* Desrd D : Le délai souhaité que le système interne vise. Le délai réel est fréquemment ajusté pour trouver un bon équilibre entre latence et fluidité.
* Intrvl : Le temps entre l'envoi des données synchronisées de l'utilisateur.
* G : Le groupe actuel auquel l'utilisateur appartient. Le regroupement dans ce contexte est un système de réseau interne utilisé pour regrouper plusieurs objets en fonction de leur distance afin d'envoyer leurs données ensemble.
* D : Le retard actuel, ou la durée depuis laquelle vous visualisez cet utilisateur.
# Menu de débogage 5

![world-debug-views-1232152-VRChat_SVxaMmgiLC.png](/img/worlds/world-debug-views-1232152-VRChat_SVxaMmgiLC.png)

Le menu de débogage 5 affiche des graphiques liés au réseau. Ils ne sont pas étiquetés et ne sont généralement pas utiles.
:::caution Les vues de débogage mondiales supérieures à 5 sont restreintes

Par défaut, seul le créateur du monde peut accéder aux menus de débogage supérieurs à 5. Cependant, vous pouvez également autoriser les autres utilisateurs à y accéder en activant le débogage du monde dans les paramètres de votre monde sur le site web. N'oubliez pas de cliquer sur "Enregistrer les modifications" ! Les autres utilisateurs devront rejoindre à nouveau le monde pour pouvoir accéder à cette vue de débogage une fois que le débogage du monde est activé.
:::

![world-debug-views-da70084-unknown_7.png](/img/worlds/world-debug-views-da70084-unknown_7.png)

# Menu de débogage 6

![world-debug-views-b0257d6-VRChat_ZRiWB4bTU7.png](/img/worlds/world-debug-views-b0257d6-VRChat_ZRiWB4bTU7.png)

Le menu de débogage 6 affiche tous les objets en réseau dans votre monde, ainsi que diverses statistiques.
* Propriétaire : L'ID du joueur propriétaire de l'objet.
* Groupe : Le groupe actuel auquel cet objet appartient. Le regroupement dans ce contexte est un système de réseau interne utilisé pour regrouper plusieurs objets en fonction de leur distance afin d'envoyer leurs données ensemble.
* En veille : Indique si l'objet est en veille. Seuls les objets avec VRCObjectSync peuvent être en veille. Lorsqu'un objet est en veille, il cesse de transmettre des données.
* Délai : Le délai actuel de cet objet entre le propriétaire et le spectateur.
* Taille : Le nombre actuel d'octets par sérialisation de cet objet. Chaque fois qu'il doit se synchroniser, il enverra autant d'octets.
* Bps : Une approximation approximative du nombre d'octets par seconde utilisés par cet objet.
* Depuis la dernière fois : Un compteur en cours indiquant depuis combien de temps cet objet a envoyé des données pour la dernière fois.
* Intervalle : Une approximation approximative du nombre de fois par seconde où cet objet essaie de se synchroniser.
# Menu de débogage 7

![world-debug-views-6ea6192-VRChat_pWGDiXUnlh.png](/img/worlds/world-debug-views-6ea6192-VRChat_pWGDiXUnlh.png)

Le menu de débogage 7 affiche les mêmes informations que le menu 6, mais filtrées et triées pour mettre en évidence les objets ayant le plus d'impact sur le réseau en premier.
# Menu de débogage 8

![world-debug-views-88ea4e6-VRChat_6e9Vhf8jnq.png](/img/worlds/world-debug-views-88ea4e6-VRChat_6e9Vhf8jnq.png)

Le menu de débogage 8 superpose un panneau sur chaque objet synchronisé dans le monde. Chaque panneau affiche diverses statistiques sur cet objet spécifique.
* P : Ping du propriétaire
* Q : Qualité des données (100% signifie qu'aucun paquet n'est perdu)
* O : ID du joueur propriétaire de l'objet
* G : Le groupe actuel auquel cet objet appartient. Le regroupement dans ce contexte est un système de réseau interne utilisé pour regrouper plusieurs objets en fonction de leur distance afin d'envoyer leurs données ensemble.
* Tenu : Indique si cet objet est tenu, s'il s'agit d'un objet à ramasser
* État : Affiche diverses informations sur ce que fait cet objet, telles que `Doit dormir`, `Joueur`, `Tenu` ou `Discontinuité`