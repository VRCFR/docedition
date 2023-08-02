
Avec Udon, vous pouvez modifier la façon dont un joueur entend la voix des autres joueurs et les sons de l'avatar. Par exemple, ce graphique permet de réduire le volume d'un joueur en réglant son gain à 5 dB (inférieur à la valeur par défaut de 15 dB) :
![player-audio-8e50220-setvoicegain.png](/img/worlds/player-audio-8e50220-setvoicegain.png)

Voici toutes les propriétés auxquelles vous pouvez accéder :

# Voix

### Régler le gain de la voix
*en décibels, plage 0-24*
Ajoutez une amplification à la voix du joueur en décibels. La valeur par défaut est de 15.

### Définir la distance proche de la voix
*en mètres, plage 0 - 1 000 000*
Le rayon proche, en mètres, où le volume commence à diminuer. Il est fortement recommandé de laisser la valeur Proche à zéro pour plus de réalisme et une spatialisation efficace des voix des utilisateurs.

### Définir la distance éloignée de la voix
*en mètres, plage 0 - 1 000 000*
Cela définit la limite de la plage pour entendre la voix de l'utilisateur. La valeur par défaut est de 25 mètres. Vous pouvez la réduire pour limiter la portée de la voix d'un autre joueur, jusqu'à 0 pour effectivement 'muet' le joueur.

### Définir le rayon volumétrique de la voix
*en mètres, plage 0 - 1 000*
La valeur par défaut est de 0.
La voix d'un joueur est normalement simulée comme une source ponctuelle, mais en modifiant cette valeur, la source peut sembler provenir d'une zone plus large. Cela doit être utilisé avec prudence et surtout pour les sources audio lointaines qui doivent sembler "grandes" lorsque vous les dépassez. **Conservez cette valeur à zéro à moins de savoir ce que vous faites.** La valeur du rayon volumétrique doit toujours être inférieure à la distance éloignée de la voix.

Si vous voulez que la voix d'un utilisateur semble proche, quelle que soit la distance, augmentez la plage de la distance proche de la voix à une grande valeur.

### Activer/désactiver le passe-bas de la voix
*Activé/désactivé*
Lorsqu'une voix est à une certaine distance, elle passe par un filtre passe-bas pour aider à comprendre dans des environnements bruyants. Vous pouvez désactiver cette option si vous souhaitez ignorer ce filtre. Par exemple, si vous voulez qu'un joueur utilise son canal vocal pour jouer un mix DJ de haute qualité, il est conseillé de désactiver ce filtre.

# Avatar

### Définir le gain audio de l'avatar
*en décibels, plage 0-10*
Définissez le gain maximum autorisé sur l'audio de l'avatar. La valeur par défaut est de 10.

### Définir le rayon éloigné audio de l'avatar
*en mètres, plage non limitée*
Cela définit le maximum de la plage pour entendre l'audio de l'avatar. La valeur par défaut est de 40 mètres. Vous pouvez la réduire pour limiter la portée de l'avatar d'un autre joueur, jusqu'à 0 pour effectivement 'muet' le joueur. Notez que cela est comparé à la distance maximale de la source audio et que la plus petite valeur est utilisée.

### Définir le rayon proche audio de l'avatar
*en mètres, plage non limitée*
Cela définit le début maximum de la plage pour entendre l'audio de l'avatar. La valeur par défaut est de 40 mètres. Vous pouvez la réduire pour limiter la portée de l'avatar d'un autre joueur, jusqu'à 0 pour effectivement 'muet' le joueur. Notez que cela est comparé à la distance minimale de la source audio et que la plus petite valeur est utilisée.

### Définir le rayon volumétrique audio de l'avatar
*en mètres, plage non limitée*
La source audio de l'avatar est normalement simulée comme une source ponctuelle, mais en modifiant cette valeur, la source peut sembler provenir d'une zone plus large. Cela doit être utilisé avec prudence et surtout pour les sources audio lointaines qui doivent sembler "grandes" lorsque vous les dépassez. Conservez cette valeur à zéro à moins de savoir ce que vous faites. La valeur du rayon volumétrique doit toujours être inférieure au rayon éloigné audio de l'avatar. La valeur par défaut est de 40 mètres.

### Forcer la spatialisation audio de l'avatar
*Activé/désactivé*
Si cette option est activée, la spatialisation est activée pour la source et le spatialBlend est réglé sur 1. La valeur par défaut est désactivée.

### Utiliser une courbe audio personnalisée pour l'avatar
*Activé/désactivé*
Cela définit si la source audio doit utiliser une courbe personnalisée préconfigurée. La valeur par défaut est désactivée.