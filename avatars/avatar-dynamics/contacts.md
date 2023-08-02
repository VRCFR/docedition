

Contacts sont un nouveau système qui permet aux avatars de détecter les collisions avec eux-mêmes ou d'autres avatars. Ces collisions peuvent ensuite être utilisées pour piloter le contrôleur d'animation et réaliser toutes sortes d'effets amusants. 

Ces contacts sont distincts des colliders standard d'Unity. Les contacts sont divisés en émetteurs et récepteurs. Les émetteurs existent simplement pour être détectés. Les récepteurs détectent les émetteurs, puis mettent à jour les paramètres en conséquence.

# VRCContactSender
Le composant Contact Sender définit un volume d'espace qui enverra un signal de contact lorsqu'il entrera en contact avec un Contact Receiver.
![contacts-59b6e82-2022-04-19_11-53-01_Unity.png](/img/avatars/contacts-59b6e82-2022-04-19_11-53-01_Unity.png)
`Transform Parent` - Transform sur lequel ce contact est placé. S'il n'est pas spécifié, nous utilisons le transform de cet objet.

## Forme
Cette section contient les paramètres qui définissent la forme du Contact Sender.
`Type de forme` - Type de forme de collision utilisé par ce contact. Vous pouvez choisir entre une sphère et une capsule.
`Rayon` - Taille du collider à partir de son origine.
`Hauteur` - Hauteur de la capsule le long de l'axe choisi.
`Position` - Décalage de position par rapport au transform parent.
`Rotation` - Décalage de rotation par rapport au transform parent.

## Filtrage
Cette section contient les paramètres permettant d'ajuster et de définir comment ce Contact Sender interagira avec les [Contact Receivers](/avatars/avatar-dynamics/contacts#VRCContactReceiver).

`Tags de collision` - Liste de chaînes de caractères spécifiant ce qui peut être affecté ou être affecté par le contact. Pour qu'une collision réussisse, l'émetteur et le récepteur doivent avoir au moins une paire de chaînes correspondantes. Les tags de collision sont sensibles à la casse.

Par exemple, les tags ci-dessous feront en sorte que le Sender envoie un signal de contact lorsqu'il entre en contact avec le Contact Receiver de la tête par défaut ou avec un Contact Receiver personnalisé portant le tag `Face` - notez la majuscule F !
![contacts-de34d55-2022-04-19_11-53-34_NVIDIA_Share.png](/img/avatars/contacts-de34d55-2022-04-19_11-53-34_NVIDIA_Share.png)
## Standard Colliders
Un ensemble de "Standard Colliders" est défini dans le Descripteur d'Avatar, dans une nouvelle section appelée "Colliders". Cette section vous permet de définir un certain nombre de colliders standard qui existent sur chaque avatar. Ils seront configurés automatiquement si vous ne les modifiez pas, mais ils peuvent également être ajustés pour correspondre exactement à votre avatar. Ces colliders n'affectent pas la note de performance.

- Tête
- Torse
- Mains G/D
- Pieds G/D
- Doigts G/D
  - Index
  - Majeur
  - Annulaire
  - Auriculaire

Ces colliders agissent principalement comme des Contact Senders que les autres personnes peuvent détecter avec leurs avatars. Cependant, les colliders des doigts et des mains sont également utilisés pour créer des colliders globaux [PhysBone](/avatars/avatar-dynamics/physbones) qui peuvent être utilisés pour affecter les PhysBones des autres personnes.

# VRCContactReceiver
Le composant Contact Receiver définit un volume d'espace qui recevra un signal de contact lorsqu'il entrera en contact avec un Contact Sender. Il ajustera ensuite un [Paramètre d'Animateur](/avatars/animator-parameters) d'une certaine manière, telle que définie par l'utilisateur.
![contacts-6f84ac4-2022-04-19_11-57-25_NVIDIA_Share.png](/img/avatars/contacts-6f84ac4-2022-04-19_11-57-25_NVIDIA_Share.png)
`Transform Parent` - Transform sur lequel ce contact est placé. S'il n'est pas spécifié, nous utilisons le transform de cet objet.

## Forme
Cette section contient les paramètres qui définissent la forme du ContactReceiver.
`Type de forme` - Type de forme de collision utilisé par ce contact. 
`Rayon` - Taille du collider à partir de son origine.
`Hauteur` - Hauteur de la capsule le long de l'axe choisi.
`Position` - Décalage de position par rapport au transform parent.
`Rotation` - Décalage de rotation par rapport au transform parent.
`Tags de collision` - Liste de chaînes de caractères spécifiant ce qui peut être affecté ou être affecté par le contact. Pour qu'une collision réussisse, l'émetteur et le récepteur doivent avoir au moins une paire de chaînes correspondantes. Les tags de collision sont sensibles à la casse.

## Filtrage
Cette section contient les paramètres permettant d'ajuster et de définir comment ce ContactReceiver interagira avec les [ContactSenders](/avatars/avatar-dynamics/contacts#VRCContactSender).

`Autoriser soi-même` - Permet à ce contact d'être affecté par vous-même.
`Autoriser les autres` - Permet à ce contact d'être affecté par d'autres personnes.
`Local uniquement` - Limite ce contact à n'être utilisé que sur le client local.

`Tags de collision` - Liste de chaînes de caractères spécifiant ce qui peut être affecté ou être affecté par le contact. Pour qu'une collision réussisse, l'émetteur et le récepteur doivent avoir au moins une paire de chaînes correspondantes. Les tags de collision sont sensibles à la casse.

## Récepteur
Cette section contient les paramètres définissant ce que le Récepteur fait lorsqu'il reçoit un signal.
`Type de récepteur` définit le comportement de la configuration du paramètre lorsqu'un signal est reçu.
- `Constant` - Vous informe de la présence de contacts. Réinitialise lorsque aucun contact n'est détecté. Idéalement, utilisez ici un paramètre booléen. Définit `1.0` pour un Float, `True` pour un Booléen et `1` pour un Entier.
- `OnEnter` - Vous informe de l'image à laquelle un contact est détecté. Réinitialise immédiatement l'image suivante. Idéalement, utilisez ici un paramètre booléen. Définit `1.0` pour un Float, `True` pour un Booléen et `1` pour un Entier. Peut éventuellement avoir une `Vélocité minimale` définie.
- `Proximité` - Vous donne une valeur Float de `0.0-1.0` dépendant de la proximité d'un contact par rapport au centre du déclencheur. Cela est calculé comme le point le plus proche de l'émetteur sur le récepteur. Vous devez utiliser un Float. S'il détecte plusieurs contacts, il vous donnera le plus proche. 
:::note

Si vous souhaitez avoir une mesure plus précise de la proximité, vous devez ajuster le rayon de l'Émetteur pour qu'il soit très petit.
:::
`Paramètre` - Le paramètre mis à jour sur le contrôleur d'animation. Ce paramètre N'A PAS besoin d'être défini dans la liste des paramètres synchronisés de l'Avatar. Le paramètre peut être un Float, un Booléen ou un Entier, selon le Type de Récepteur utilisé.
`Valeur` - Valeur à laquelle le paramètre est mis à jour lorsqu'une collision est détectée. Le paramètre sera réinitialisé à zéro lorsqu'il n'y a pas de collisions présentes.
`Vélocité minimale` - Vitesse minimale nécessaire à partir d'un collider entrant pour affecter ce déclencheur, uniquement active dans le type `OnEnter`.