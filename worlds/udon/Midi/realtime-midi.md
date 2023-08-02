

# Realtime Midi

Vous pouvez utiliser des dispositifs MIDI pour contrôler votre monde Udon en temps réel en utilisant des notes MIDI et des changements de contrôleur.

## Composants

Pour commencer avec Midi dans votre scène, ajoutez un composant **VRC Midi Listener** à l'un de vos objets GameObject.

![VRCMidiListener](/img/worlds/realtime-midi-215557542-bf65a6ef-47d0-4e2f-8d39-337847db461c.png)

Ce composant informe VRChat que vous souhaitez recevoir des événements MIDI et lance le système MIDI si nécessaire. **Vous devez sélectionner les événements que vous souhaitez recevoir** en activant les bascules d'événements actifs pour les sélectionner - aucun événement n'est sélectionné par défaut, alors activez-les avant de commencer les tests. **Vous devez également choisir un UdonBehaviour** qui recevra ces événements en le sélectionnant comme "Behaviour" sur le VRC Midi Listener. Cet UdonBehaviour peut être sur le même GameObject que le Listener MIDI, ou sur tout autre objet.

Lorsque vous démarrez votre scène, vous pouvez remarquer un GameObject **VRCMidiHandler** qui est ajouté automatiquement. Celui-ci gère le pilote du dispositif MIDI et envoie des événements à tous les Listeners. NE PAS ajouter ce composant vous-même - il est conçu pour être ajouté et supprimé automatiquement afin que les dispositifs MIDI ne soient connectés qu'une seule fois, et déconnectés lorsque quelqu'un quitte votre monde.

## Sélection du dispositif - Éditeur

Vous pouvez tester vos événements MIDI dans l'éditeur Unity en sélectionnant votre dispositif via le SDK de VRChat. Il est enregistré dans vos préférences de l'Éditeur, donc Unity se souviendra de votre dispositif pour chaque projet.

![Midi Utility Window](/img/worlds/realtime-midi-215557576-5414eb63-a857-4334-8a8c-05f3b6436773.png)

![Midi Utility Selector](/img/worlds/realtime-midi-215557616-8cc3fd99-0fe4-4564-9413-cc805708cf89.png)

## Sélection du dispositif - Exécution

Lorsque vous visitez un monde avec des événements MIDI, VRChat essaiera d'ouvrir le premier dispositif MIDI qu'il peut trouver sur votre machine. Si vous avez plusieurs dispositifs et que vous souhaitez spécifier lequel utiliser, vous pouvez passer une partie de son nom en tant qu'argument de ligne de commande. Par exemple, si vous avez un dispositif qui apparaît dans Windows comme "SchneebleCo MidiKeySmasher 89", vous pouvez l'ajouter à vos options/de script de lancement comme ceci :
``--midi=midikeysmasher`
VRChat fera correspondre les noms partiels et ignorera la casse. Apprenez-en plus sur toutes les autres Options de Lancement : [Options de Lancement](https://docs.vrchat.com/docs/launch-options)

## Exemple de scène

Vous pouvez télécharger une scène de démo qui lit et affiche les trois types de messages ici : [Téléchargement de la scène de démo](https://www.dropbox.com/s/83zili4e8lkszu7/MidiCubeExample_v4.unitypackage)
Vous pouvez visiter le monde ici : [Udon Midi Test](https://vrchat.com/home/world/wrld_f8bc6485-dcdf-4646-89d8-14e4772561ee).