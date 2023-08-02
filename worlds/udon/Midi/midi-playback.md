

Vous pouvez lire des données MIDI avec une piste audio pour contrôler ce que vous voulez dans votre monde Udon. Vous pouvez accéder à la [scène d'exemple](#example-midiplaybackscene) pour commencer immédiatement.

## Ressources : Fichier MIDI et AudioClip

Les fichiers avec l'extension .mid sont traités en tant que ressources MIDI. Pour commencer avec vos propres fichiers MIDI et audio :
1. Faites glisser et déposez-les quelque part dans votre dossier Ressources. Le fichier MIDI doit avoir l'extension .mid, le fichier audio peut être de n'importe quel [type pris en charge par Unity](https://docs.unity3d.com/Manual/class-AudioClip.html) (.aif, .wav, .mp3, .ogg).
2. Sélectionnez le fichier MIDI et associez-le à son AudioClip correspondant.

![image](/img/worlds/midi-playback-214464414-32af9c18-c003-49ed-bd12-dd431367db56.png)

3. Il est impératif que le BPM de votre fichier MIDI soit correctement configuré. Si les données semblent ne pas correspondre à l'audio, c'est probablement le problème. Vous pouvez remplacer le BPM ici en activant "Override Bpm" et en fournissant la bonne valeur. Il serait encore mieux de modifier votre fichier MIDI et d'ajouter le BPM correct.


## Composant : VRCMidiPlayer

![VRCMidiPlayer](/img/worlds/midi-playback-215556799-a546e119-afdb-441f-8019-70ee50b6c008.png)

C'est le cerveau de l'opération. Il fonctionne de manière similaire à une source audio, mais utilise une ressource MIDI à la place. Il envoie des événements MIDI [Note On](/worlds/udon/midi#midinoteon) et [Note Off](/worlds/udon/midi#midinoteoff) à tous les UdonBehaviours cibles.

### Champs de l'inspecteur

<dl>
<dt>Fichier MIDI</dt>
<dd>Le fichier MIDI au format SMF dont vous souhaitez déclencher les données.</dd>
<dt>Source audio</dt>
<dd>Le composant AudioSource avec le clip audio correspondant à vos données MIDI.</dd>
<dt>Comportements cibles</dt>
  <dd>Un tableau de UdonBehaviours auxquels des événements MIDI <a href="/worlds/udon#midinoteon">Note On</a> et <a href="/worlds/udon#midinoteoff">Note Off</a> seront envoyés</dd>
<dt>Afficher les blocs de débogage</dt>
<dd>Lorsqu'il est activé, vous pouvez voir l'affichage de toutes les notes de votre fichier MIDI actuel dans la vue de scène de l'éditeur Unity pendant que le VRCMidiPlayer est sélectionné. Utile pour un aperçu rapide de vos données.</dd>
</dl>

### Méthodes

<dl>
<dt>Play()</dt>
<dd>Démarre la lecture des événements MIDI et de la source audio.</dd>
<dt>Stop()</dt>
<dd>Arrête la lecture des événements MIDI et de la source audio.</dd>
</dl>

### Propriétés

<dl>
<dt>`float` time</dt>
<dd>Définit et obtient le temps actuel des sources MIDI et audio.</dd>
<dt>`MidiData` midiData</dt>
<dd>Obtient un objet MidiData contenant toutes les données de la piste MIDI actuelle. Peut être utilisé avant la lecture pour mettre en place les choses.</dd>
</dl>

## Exemple : MidiPlaybackScene

https://user-images.githubusercontent.com/737888/214626843-53a4c069-ea69-423a-926d-e2ce024c9819.mp4

Le SDK comprend un exemple simple de lecture de fichiers MIDI. Vous pouvez le charger depuis la barre de menu sous VRChat SDK > Samples > MidiPlayback.

Après avoir chargé la scène, appuyez sur "Play" dans Unity pour voir et entendre la lecture MIDI ! Au fur et à mesure que la courte boucle est jouée, des images de couleurs différentes clignoteront en rythme avec la musique.

Les objets importants de la scène sont le VRCMidiPlayer et le MidiGrid.

### VRCMidiPlayer

Ce GameObject possède un composant VRCMidiPlayer ainsi qu'un AudioSource, et ils sont tous configurés avec un exemple de fichier MIDI et d'AudioClip. Il a le MidiGrid défini comme son unique targetBehaviour.

### MidiGrid

Ce GameObject possède un UdonBehaviour pour recevoir les événements MIDI, ainsi que plusieurs toiles en tant qu'enfants.

Chaque toile a une "Grille" avec 12 composants Image enfants. Ces images seront activées et désactivées lorsque des notes MIDI sont jouées. Une octave comporte 12 notes, ce qui permet de visualiser chaque note sous forme d'une image séparée.

### Programme MidiGrid

#### Échange des données

Si vous avez des fichiers MIDI et audio, vous pouvez les importer et remplacer les ressources existantes par les vôtres pour voir à quoi elles ressemblent dans la scène.

#### Modification des canaux

Le programme MidiGrid a une variable appelée "channels". Cet tableau fait correspondre les canaux des données MIDI aux grilles à l'écran. Par défaut, l'ordre est "3 4 1 2". Cela signifie que la première grille affichera les données du canal 3, la deuxième grille affichera le canal 4, etc. Vous pouvez modifier l'ordre ici pour modifier légèrement les visuels.

Si vous chargez votre propre fichier de données MIDI, vous pouvez vérifier la console Unity pour voir les canaux et les notes qui sont joués. Chaque événement Note On affichera un message tel que "3:75". Cela vous montre que le canal 3 a joué la note 75.

#### Ajout de grilles

Si vous souhaitez utiliser une chanson avec plus de 4 canaux, vous pouvez dupliquer les grilles et les ajouter à la variable `grids` du programme. N'oubliez pas d'ajouter plus de `channels` également !

#### Le programme complet, expliqué.

Voici une explication de ce qui se passe dans le programme MidiGrid.

**Événement de démarrage :**
![image](/img/worlds/midi-playback-214465917-450d04cc-e7ce-4551-a3cd-f4feddd124b2.png)

Au démarrage, il passe en revue chaque objet du tableau `grids`, trouve le composant 'Image' sur son enfant et définit sa valeur `enabled` sur `false`, masquant ainsi toutes les images au démarrage.

Il attend également 1 seconde après le chargement, puis appelle `Play()` sur le VRCMidiPlayer pour démarrer la musique et le flux de données.

**Événements de notes :**

![image](/img/worlds/midi-playback-214465984-fea32000-04c3-42f3-bf7f-cef471d2b46f.png)

Lorsqu'il reçoit un événement `Note On` MIDI, il parcourt chaque entrée du tableau `channels` et vérifie si le canal de la note entrante correspond à l'une des entrées. Si une correspondance est trouvée, ce nombre est utilisé comme `index` pour le tableau `grids`, afin de trouver la grille correspondante. La note entrante est soumise à `int.Remainder()` pour trouver son index dans l'octave - un Do est 0, un Do# est 1, etc. Cet index est utilisé pour trouver le bon enfant de la grille, puis pour définir `enabled` sur `true` pour l'élément 'Image'. Enfin, le canal de la note et le numéro de la note sont enregistrés dans la console.

Lorsque le script reçoit un événement `Note Off` MIDI, il effectue un processus similaire à celui décrit ci-dessus. Pour masquer à nouveau le composant 'Image', il définit `