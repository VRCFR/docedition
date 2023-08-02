

:::caution

Cette page est significativement dépassée, mais devrait être en grande partie exacte.
:::
## Paramètres d'exportation

Lors de l'exportation de votre rig depuis votre éditeur 3D de choix, assurez-vous que vos paramètres de coordonnées sont corrects. La plupart du temps, les valeurs par défaut sont correctes.

Pour Blender, assurez-vous que la rotation X de repos est de 90 degrés.
### Rig humanoïde
Unity signalera une configuration erronée de votre rig humanoïde si elle ne répond pas aux exigences de Mecanim pour un rig humanoïde. Veuillez lire et vous familiariser avec la [documentation Unity sur la configuration des avatars](https://docs.unity3d.com/Manual/ConfiguringtheAvatar.html).

:::danger Un avatar humanoïde doit avoir des os de tête, de mains et de pieds mappés.

Vous verrez ce message depuis le panneau de contrôle de construction VRChat si votre rig d'avatar est humanoïde mais ne possède pas les os essentiels mappés.
:::

:::note Avatars non-humains

Si votre avatar diffère grandement d'un humain (par exemple, un quadrupède, un monstre voûté, etc.), vous devriez envisager d'utiliser un rig générique et votre propre Contrôleur d'Animation. Consultez le SimpleAvatarController pour un exemple. Ceci est plus avancé que la création d'un avatar humanoïde, vous devez donc être très familier avec le système du Contrôleur d'Animation d'Unity.
:::

### Mappage des doigts

:::caution Si les os des pouces, des index et des majeurs ne sont pas mappés, la fonction Full-Body IK sera désactivée.

**Cet avertissement n'apparaît pas pour les avatars du SDK3, car ils n'ont aucun problème à utiliser des armatures sans os de doigts.** Cette erreur ne se produit que lors de l'utilisation du SDK VRChat2, qui est obsolète et ne doit pas être utilisé.\n\nPour bénéficier de la pleine IK (permettant de se baisser et de placer automatiquement les pieds), vous devez avoir ces trois os de doigts mappés. Si vous ignorez cet avertissement, votre avatar ne pourra pas se baisser et ses pieds ne se placeront pas automatiquement (sauf si vous utilisez un déplacement par le contrôleur).\n\nCela empêchera également la lecture des remplacements d'animation personnalisés sur les gestes de la main. (Ceci n'est pas actuellement mentionné par l'avertissement du SDK.)
:::

### Hiérarchie de la colonne vertébrale

:::danger Votre rig a le torse supérieur (Upper Chest) mappé dans le rig humanoïde. Cela causera des problèmes avec l'IK.

**Cet avertissement n'apparaît pas pour les avatars du SDK3, car ils n'ont aucun problème à utiliser des armatures avec un torse supérieur mappé.** Cette erreur ne se produit que lors de l'utilisation du SDK VRChat2, qui est obsolète et ne doit pas être utilisé.\n\nSi vous devez utiliser le SDK2, laissez l'os du torse supérieur vide lors de la configuration de votre rig humanoïde.
:::

:::danger Des éléments manquent dans la hiérarchie de la colonne vertébrale. Assurez-vous que le bassin, la colonne vertébrale, le torse, le cou et les épaules sont mappés.

Ces os doivent tous être mappés. Si vous obtenez ce message, assurez-vous que ces emplacements ne sont pas vides. Notez que les emplacements du cou et du torse sont facultatifs pour Mecanim, mais nécessaires pour VRChat.
:::

:::danger La hiérarchie de la colonne vertébrale est incorrecte. Assurez-vous que le parent des épaules et du cou est le torse.

Pour que l'IK fonctionne correctement, vous devez avoir une hiérarchie spécifique d'os autour du torse. Dans votre rig, vos os d'épaule (mappés dans le slot Bras gauche > Épaule, Bras droit > Épaule) doivent être des enfants directs de votre os de torse (mappé dans le slot Corps > Torse). De plus, l'os du cou (mappé dans le slot Tête > Cou) doit également être un enfant direct du torse.
:::

### Hiérarchie des bras et des jambes

:::caution Le LowerArm (avant-bras) n'est pas le premier enfant de l'UpperArm (bras supérieur) ou la Main n'est pas le premier enfant du LowerArm (avant-bras) : vous pouvez rencontrer des problèmes avec les rotations de l'avant-bras.

Le système IK de VRChat examine le premier enfant d'un os pour déterminer la disposition des os. Si vous avez d'autres os enfants, comme des os de placement d'accessoires ou des os de torsion dans votre rig, ils peuvent perturber l'IK. Dans ce cas particulier, le SDK détecte que votre LowerArm n'est pas le premier enfant répertorié de votre os UpperArm.\n\nPour résoudre ce problème, déplacez l'os enfant en première position dans la liste des enfants de l'os parent. **Vous devrez déballer votre prefab d'avatar pour cela.**\n\nNotez que ce message nomme l'emplacement, pas le nom de l'os réel dans votre rig, vous devrez donc regarder pour voir quel os se trouve dans cet emplacement.
:::

:::caution Le LowerLeg (jambe inférieure) n'est pas le premier enfant de l'UpperLeg (cuisse) ou le Foot (pied) n'est pas le premier enfant du LowerLeg (jambe inférieure) : vous pouvez rencontrer des problèmes avec les rotations du tibia.

Voir ci-dessus.
:::

### Hiérarchie générale

:::caution Cet avatar possède une hiérarchie divisée (l'os Hips n'est pas l'ancêtre de tous les os humanoïdes). L'IK peut ne pas fonctionner correctement.

Certains rigs divisent la hiérarchie en deux sections, le haut et le bas du corps. Dans ce cas, l'os que vous placez dans le slot Corps > Hanches doit être l'ancêtre (parent ou supérieur) du reste des os humains que vous mappez. Soyez très prudent avec ces types de rigs ! Souvent, l'ancêtre de ces os est un os racine sur le sol ou un autre emplacement qui est un mauvais emplacement pour un os de hanche. Beaucoup de ces rigs ne conviennent pas à l'utilisation avec VRChat et doivent être retravaillés pour fonctionner correctement.
:::

### Suivi du corps entier
Il y a des considérations spéciales si vous utilisez le suivi du corps entier, c'est-à-dire si vous avez 3 HTC Tracking Pucks connectés. Il existe plusieurs recommandations qui garantiront que votre avatar fonctionne bien lors de l'utilisation du suivi du corps entier.

Pour plus d'informations détaillées sur les exigences de rigging pour le suivi du corps entier, consultez notre [guide du système Full-Body Tracking](https://docs.vrchat.com/docs/full-body-tracking).
:::caution L'angle entre le bassin et les os de la cuisse doit être proche de 180 degrés (l'angle de cet avatar est de ___). Votre avatar risque de ne pas fonctionner correctement avec l'IK et le tracking du corps entier.

Le suivi du corps entier est sensible à l'angle entre l'os de la hanche et les os de la cuisse. Il est préférable de mesurer cet angle lorsque l'AvatarTPoseController est appliqué à votre avatar. Idéalement, l'os de la hanche est dirigé vers le haut et les os de la cuisse sont dirigés vers le bas dans la position TPose, mais une légère divergence est acceptable. Vous pouvez ignorer ce message si vous n'allez pas utiliser le suivi du corps entier.
:::

### Os des orteils
Il n'est pas nécessaire de mapper les os des orteils dans un avatar humanoïde. Cependant, si vous LES mappez, votre avatar pourra monter et descendre sur la pointe des pieds. Le mappage des orteils rend également le placement automatique des pieds plus naturel, ainsi qu'améliore l'apparence de l'équilibre en alignant la position auto sur le début de l'os des orteils plutôt que sur le talon.