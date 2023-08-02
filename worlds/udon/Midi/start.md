

Depuis les années 1980, le MIDI a permis de connecter les instruments de musique de manière imaginative. Nous l'avons inclus dans VRChat afin que vous puissiez créer des mondes qui réagissent aux instruments en temps réel et aux performances préenregistrées.

>En savoir plus sur le [MIDI sur Wikipedia](https://fr.wikipedia.org/wiki/MIDI).

![image](/img/worlds/index-215557268-2d85f551-8fff-4990-a95a-c8a2d412d6a2.png)

Il existe deux façons de travailler avec le MIDI dans vos mondes Udon :
- ## [Temps réel](./realtime-midi) à partir d'un instrument connecté à votre ordinateur.
- ## [Lecture](./midi-playback) des données MIDI avec des fichiers audio.

Quelle que soit la méthode choisie, vous travaillerez avec les événements MIDI d'Udon, détaillés ci-dessous.

## Événements MIDI

### MidiNoteOn
Déclenché lorsqu'un message "Note On" est reçu. Il peut être déclenché soit par la lecture MIDI, soit en appuyant sur une touche/bouton de votre appareil.
Sorties :
* `int channel` Canal MIDI qui a reçu l'événement, de 0 à 15.
* `int number` Numéro de note de 0 à 127 (votre appareil MIDI peut ne pas envoyer toute la plage)
* `int velocity` Nombre de 0 à 127 représentant la vitesse à laquelle la note a été déclenchée, si pris en charge par votre appareil MIDI.

### MidiNoteOff
Déclenché lorsqu'un message "Note Off" est reçu, généralement en relâchant une touche/bouton de votre appareil.
Sorties :
* `int channel` Canal MIDI qui a reçu l'événement, de 0 à 15.
* `int number` Numéro de note de 0 à 127 (votre appareil MIDI peut ne pas envoyer toute la plage)
* `int velocity` Cette valeur est généralement 0 pour les événements Note Off, mais peut varier en fonction de votre appareil.

### MidiControlChange
Déclenché lorsqu'un changement de contrôle est reçu. Ces événements sont généralement envoyés par les boutons et les curseurs de votre appareil MIDI.
Sorties :
* `int channel` Canal MIDI qui a reçu l'événement, de 0 à 15.
* `int number` Numéro de contrôle de 0 à 127.
* `int value` Nombre de 0 à 127 représentant la valeur envoyée par votre contrôleur. Pour certains boutons qui peuvent tourner indéfiniment plutôt que d'être limités par des positions de départ/fin physiques, cette valeur peut être simplement de 0 et 1 ou une autre plage indiquant des incréments "positifs" et "négatifs" que vous devez gérer vous-même.