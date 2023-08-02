
## Déclencheurs

Si vous souhaitez détecter quand un joueur entre ou sort d'une zone, la meilleure solution est d'utiliser les événements **OnPlayerTrigger**. Il en existe trois :

- **OnPlayerTriggerEnter** est appelé lorsque la capsule d'un joueur entre dans un déclencheur de collision
- **OnPlayerTriggerStay** est appelé à chaque image lorsque la capsule d'un joueur est à l'intérieur d'un déclencheur de collision
- **OnPlayerTriggerExit** est appelé lorsque la capsule d'un joueur sort d'un déclencheur de collision.

![Un simple Collider de type Box avec la case 'Is Trigger' cochée.](/img/worlds/player-collisions-6d9aaf6-trigger-collider.png)
Pour utiliser ces événements, ajoutez un objet avec un collider et cochez la case 'Trigger' sur le collider. Un déclencheur de collision permet aux objets et aux joueurs de le traverser et appelle des événements lorsque ces objets entrent en collision. Vous pouvez en savoir plus sur les [collisions dans le manuel Unity](https://docs.unity3d.com/2019.4/Documentation/Manual/CollidersOverview.html).

:::note

Il y a quelques cas particuliers où l'un de ces événements pourrait être omis, comme lorsque le joueur se téléporte hors du collider ou se déplace TRÈS rapidement. Nous ajouterons une gestion à l'avenir pour capturer ces cas.
:::

### Physique
Il existe un autre ensemble d'événements que vous pouvez utiliser lorsque vous avez des objets comme des balles rebondissantes ou des projectiles que vous déplacez avec la physique. Ces objets ont des colliders avec IsTrigger désactivé afin qu'ils interagissent avec l'environnement et entre eux.

Pour détecter des événements sur ces colliders, vous pouvez utiliser :
- **OnPlayerCollisionEnter** est appelé lorsque la capsule d'un joueur entre en collision avec un collider.
- **OnPlayerCollisionStay** est appelé à chaque image lorsque la capsule d'un joueur est à l'intérieur d'un collider.
- **OnPlayerCollisionExit** est appelé lorsque la capsule d'un joueur sort d'un collider.

:::caution

Ces événements NE SERONT PAS appelés lorsque le joueur 'rentre dans' un objet stationnaire. Si vous souhaitez gérer cela, utilisez un déclencheur de collision.
:::

### Particules
Enfin, vous pouvez utiliser **OnPlayerParticleCollision** pour détecter quand une particule entre en collision avec un joueur, à condition que le système de particules ait la collision activée et envoie des messages de collision.
![Ce système de particules a le module Collision activé, est réglé sur les modes 'Monde' et '3D', avec 'Envoyer les messages de collision' activé.](/img/worlds/player-collisions-40d1f44-particle-collisions.png)

### Exemples
![Consultez la scène d'exemple Udon pour voir comment ces événements peuvent être utilisés.](/img/worlds/player-collisions-f98c33a-udonexamplescene-collisions.png)