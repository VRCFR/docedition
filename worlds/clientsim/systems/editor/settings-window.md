

# Fenêtre des paramètres

La fenêtre des paramètres affiche tous les [paramètres de ClientSim](../runtime/settings.md) qui peuvent être modifiés. Certaines de ces valeurs ne peuvent pas être modifiées pendant l'exécution. Il y a aussi un bouton pour créer des joueurs à distance et un champ de texte pour donner à ces joueurs à distance un nom personnalisé.
La fenêtre des paramètres peut être ouverte via l'option "VRChat SDK/Utilities/ClientSim".

## Avertissements de configuration de projet

Si les paramètres du projet Unity ne correspondent pas à ce qui est nécessaire pour exécuter ClientSim, des avertissements s'afficheront pour chaque paramètre de projet non valide.

## Configuration des paramètres du projet

ClientSim nécessite des paramètres spécifiques du projet Unity pour fonctionner correctement. Ces paramètres ne sont pas par défaut pour un projet et nécessitent une action de l'utilisateur pour les modifier. La fenêtre des paramètres de ClientSim affichera les paramètres de projet incorrects actuels avec des boutons pour mettre à jour le projet avec les paramètres corrects. Ce comportement diffère de CyanEmu, qui, à chaque rechargement d'assemblage, forcerait automatiquement la mise à jour des paramètres du projet.

### Les paramètres du gestionnaire d'entrée sont incorrects
ClientSim requiert le nouveau système d'entrée Unity. Lors de l'importation de ce package, il demandera à l'utilisateur de l'activer et de redémarrer Unity. Aucune des options de cette boîte de dialogue n'est le paramètre correct pour ClientSim et l'utilisateur doit activer à la fois l'ancienne entrée et la nouvelle entrée. En cliquant sur le bouton "Faire ça !" dans la fenêtre des paramètres, les bonnes entrées seront configurées et Unity redémarrera.

### Les axes d'entrée diffèrent de ceux de VRChat
Bien qu'il ne soit pas utilisé dans ClientSim, cela est utile pour que les utilisateurs testent l'obtention d'entrées dans les programmes Udon.

### Le spatialiseur audio n'est pas défini
ClientSim dépend du spatialiseur audio Oculus.

### Les calques de projet et la matrice de collision ne sont pas définis
L'utilisateur doit ouvrir le panneau de contrôle de construction VRChat pour les configurer correctement.