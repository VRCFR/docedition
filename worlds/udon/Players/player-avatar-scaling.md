

Udon fournit des fonctions permettant aux créateurs de mondes de :
- Permettre ou imposer des fonctionnalités et des paramètres de redimensionnement d'avatar.
- Réagir aux changements de la hauteur du joueur.

Pour voir les événements pertinents à utiliser en concert avec ces fonctions, notamment "OnAvatarChanged" et "OnAvatarEyeHeightChanged", consultez [Événements de l'Avatar](/worlds/udon/avatar-events).

:::note[Redimensionnement et collision]
Veuillez noter que redimensionner un avatar à une autre taille n'a **aucun effet** sur sa collision avec l'environnement - tout comme le téléchargement d'un avatar que vous avez agrandi dans Unity ne le ferait pas.
:::

Le redimensionnement de l'avatar fonctionne en deux modes et peut être ajusté individuellement pour chaque joueur :

1. Un mode contrôlé par le joueur, où le joueur est autorisé à utiliser une marionnette radiale dans son menu d'actions ou un bouton "Ajuster la Hauteur des Yeux" dans son menu rapide pour ajuster sa propre hauteur.
2. Un mode autoritaire par le monde où ces fonctionnalités sont désactivées et les hauteurs des joueurs ne peuvent être définies que par un programme Udon s'exécutant dans le monde.

Dans les deux cas, les changements d'avatar et les changements de hauteur des yeux déclencheront les événements "OnAvatarChanged" et "OnAvatarEyeHeightChanged" afin qu'un programme Udon puisse réagir à ces occurrences.

:::note[Autoritaire par défaut]

Actuellement, le redimensionnement de l'avatar fonctionne en mode autoritaire par défaut. Si vous souhaitez utiliser le mode contrôlé par le joueur, vous devez l'activer sur le site web ou avec les fonctions Udon ci-dessous.
:::

## Activation du redimensionnement contrôlé par le joueur via le site web

Si vous souhaitez simplement activer le redimensionnement contrôlé par le joueur dans votre monde sans avoir à utiliser Udon et à le réimporter, vous pouvez simplement vous connecter à la [section "Mes Mondes" du site web de VRChat](https://vrchat.com/home/content/worlds), sélectionner votre monde, l'activer, et enregistrer vos modifications.

![C'est vraiment facile !](/img/worlds/udon/website_avatar_scaling_enabled.png)

## Fonctions pour le redimensionnement contrôlé par le joueur

:::note[Seulement pour le joueur local]
Sauf indication contraire, toutes les fonctions ci-dessous ne peuvent être utilisées que par un programme Udon affectant le joueur local et ne peuvent pas être appelées avec succès sur un objet `VRCPlayerApi` appartenant à un autre joueur.
:::

### GetManualAvatarScalingAllowed

Vérifie si le joueur local est autorisé à contrôler l'échelle de son avatar.

**Sortie**
- `bool` : `true` si le joueur local est en mode de redimensionnement d'avatar contrôlé par le joueur, ou `false` s'il est en mode de redimensionnement d'avatar autoritaire par le monde.

### SetManualAvatarScalingAllowed

Bascule entre les modes de redimensionnement contrôlé par le joueur et autoritaire par le monde.

**Entrée**
- `bool` : `true` active le mode contrôlé par le joueur, et `false` active le mode autoritaire par le monde.

### GetAvatarEyeHeightMinimumAsMeters

Retourne la hauteur minimale des yeux en mètres à laquelle le joueur local est autorisé à se redimensionner en mode de redimensionnement d'avatar contrôlé par le joueur. (Supérieure ou égale à 0,2 mètres.)

**Sortie**
- `float` : La hauteur minimale des yeux en mètres.

### SetAvatarEyeHeightMinimumByMeters

Définit la hauteur minimale en mètres à laquelle le joueur local est autorisé à se redimensionner en mode de redimensionnement d'avatar contrôlé par le joueur. (Doit être supérieure ou égale à 0,2 mètres.)

**Entrée**
- `float` : Définit la hauteur minimale des yeux de l'avatar en mètres.

### GetAvatarEyeHeightMaximumAsMeters

Retourne la hauteur maximale des yeux à laquelle le joueur local est autorisé à se redimensionner en mode de redimensionnement d'avatar contrôlé par le joueur. (Inférieure ou égale à 5 mètres.)

**Sortie**
- `float` : La hauteur maximale des yeux de l'avatar en mètres.

### SetAvatarEyeHeightMaximumByMeters

Définit la hauteur maximale en mètres à laquelle le joueur local est autorisé à se redimensionner en mode de redimensionnement d'avatar contrôlé par le joueur. (Doit être inférieure ou égale à 5 mètres.)

**Entrée**
- `float` : Définit la hauteur maximale des yeux en mètres.

## Fonctions pour le redimensionnement autoritaire par le monde

:::note[Seulement pour le joueur local]
Sauf indication contraire, toutes les fonctions ci-dessous ne peuvent être utilisées que par un programme Udon affectant le joueur local et ne peuvent pas être appelées avec succès sur un objet `VRCPlayerApi` appartenant à un autre joueur.
:::

### GetAvatarEyeHeightAsMeters

Retourne la hauteur des yeux configurée pour l'avatar du joueur cible. Cette fonction fonctionne pour le joueur local **et** les joueurs distants.

**Sortie**
- `float` : La hauteur des yeux configurée pour l'avatar du joueur cible.

### SetAvatarEyeHeightByMeters

**Entrée**
- `float` : Définit la hauteur des yeux en mètres pour l'avatar actuel du joueur.

### SetAvatarEyeHeightByMultiplier

**Entrée**
- `float` : Définit la hauteur des yeux comme un multiple de la hauteur des yeux de l'avatar du joueur cible à son échelle prédéfinie.