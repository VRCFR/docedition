

### GetWalkSpeed / SetWalkSpeed
*float, plage de travail autour de 0-5*
La vitesse à laquelle un joueur peut se déplacer dans votre monde. Réglez cette valeur en dessous de la vitesse de course.

### GetRunSpeed / SetRunSpeed
*float, plage de travail autour de 0-10*
La vitesse à laquelle un joueur peut courir dans votre monde. Réglez cette valeur au-dessus de la vitesse de marche.

### GetStrafeSpeed / SetStrafeSpeed
*float, plage de travail autour de 0-5*
La vitesse à laquelle un joueur peut se déplacer latéralement dans votre monde. Il est recommandé de régler cette valeur de la même manière que la vitesse de marche. Non affecté par la course.

### GetJumpImpulse / SetJumpImpulse
*float, plage de travail autour de 0-10*
La force appliquée lorsqu'un joueur saute. La valeur par défaut est 0, donc réglez cette valeur si vous souhaitez activer le saut dans votre monde. Le préfabriqué VRCWorld par défaut la règle sur 3.

### GetGravityStrength / SetGravityStrength
*float, plage de travail autour de 0-10*
Multiplicateur pour la force de gravité du monde (réglée sur la valeur par défaut de la Terre). Ne modifiez pas Physics.Gravity d'Unity dans votre projet, obtenez et réglez cette valeur ici à la place. La valeur par défaut est 1.

### Immobilize
*Boolean*
Définissez cette valeur sur true pour garder un joueur immobilisé en place, désactivant sa locomotion. Notez que les joueurs en réalité virtuelle peuvent toujours déplacer leur point de vue, mais leur avatar restera immobile.