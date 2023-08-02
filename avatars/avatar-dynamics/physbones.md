
PhysBones est un ensemble de composants qui vous permet d'ajouter un mouvement secondaire aux avatars, vous permettant d'ajouter du mouvement aux cheveux, à la queue, aux oreilles, aux vêtements et plus encore ! Bien utilisés, ils rendent votre avatar plus dynamique et réaliste.

PhysBones remplace Dynamic Bones. Bien que les deux systèmes partagent de nombreux concepts, il existe des différences majeures avec PhysBones, de sorte que tous les avatars ne peuvent pas être directement traduits vers le système de VRChat.

Un exemple d'utilisation d'Avatar Dynamics peut être trouvé dans le SDK sous `VRCSDK\Examples3\Dynamics\Robot Avatar`.

# VRCPhysBone

Définit une chaîne d'os à animer avec PhysBones. Ils peuvent être utilisés pour simuler des mouvements souples et secondaires comme les cheveux, la queue, les oreilles tombantes, etc. Il dispose de nombreuses options de configuration et peut être configuré de différentes manières.

De plus, les PhysBones peuvent être manipulés par vous et d'autres personnes ! Si vous avez donné la permission à l'autre utilisateur, d'autres personnes peuvent saisir les PhysBones configurés sur votre avatar et appuyer sur la gâchette tout en tenant le PhysBone pour le "poser" et le maintenir en position. Vous pouvez également désactiver cette fonctionnalité dans la configuration pour ne pas permettre le placement, ne pas permettre la saisie ou ne pas permettre de collisions du tout.

Bien qu'il ne soit pas conçu comme tel, PhysBones sert également de substitut raisonnable aux vêtements jusqu'à ce que nous implémentions notre propre composant de vêtement.

![](/img/avatars/physbones-ca9ee06-2022-05-04_18-23-09_Unity.png)

## Versions

Vous pouvez désormais sélectionner la version du composant VRCPhysBone que vous souhaitez utiliser directement sur le composant. Par défaut, la dernière version sera choisie lors de la création d'un nouveau composant. Les avatars existants continueront d'utiliser leur version précédente à moins d'être mis à jour manuellement et réimportés.

Version 1.0 :

- La version de base du composant VRCPhysBone.

Version 1.1 :

- Mise à jour des os souples, permettant aux os de s'étirer et d'être affectés par le mouvement.
- La gravité agit maintenant comme un rapport de la rotation des os au repos. Un tirage positif est nécessaire pour que les os se déplacent dans la direction de la gravité.
- La rigidité agit maintenant comme un rapport qui maintient un os dans son orientation précédente.

## Transformations

`Root Transform` - La transformation à partir de laquelle ce composant commence. Si elle est laissée vide, nous supposons que nous commençons à cet objet de jeu.
`Ignore Transforms` - Liste des transformations ignorées qui ne doivent pas être affectées par ce composant. Les transformations ignorées incluent automatiquement tous les enfants de cette transformation.
`Endpoint Position` - Vecteur utilisé pour créer des os supplémentaires à chaque extrémité de la chaîne. Utilisé uniquement si la valeur est différente de zéro. En général, vous voudrez l'augmenter le long de l'axe +Y, qui pointe vers le haut de l'os.
`Multi-Child Type` - Comportement de l'os racine lorsque plusieurs chaînes d'os existent. Il existe trois modes :

- Si réglé sur **Ignore**, l'os racine ne se déplacera pas et ignorera la physique. Utile pour les cheveux, par exemple, car vous pouvez utiliser un seul composant Physbone sur la racine pour affecter tous les os des cheveux !
- Si réglé sur **First**, l'os racine formera une seule chaîne continue avec la première chaîne d'os dans la hiérarchie. Toutes les autres chaînes fonctionneront toujours, mais elles partiront du premier os de chaque chaîne respective plutôt que de la racine comme la première chaîne.
- Si réglé sur **Average**, le mouvement de l'os racine sera la moyenne de tous les autres chaînes. Cela signifie que la base de chaque chaîne pourra bouger.

> 🚧
>
> Si vous utilisez un seul os racine, ou un seul os racine avec plusieurs enfants (mais pas de petits-enfants), vous **devez** définir une position finale !

Par exemple, si vous placez le composant PhysBone sur l'un des os `RootBone` ci-dessous, vous **devez** définir une **Position finale** pour que les PhysBones fonctionnent. C'est différent des Dynamic Bones !

Os unique

- `RootBone`

Plusieurs enfants, un seul parent

- `RootBone`
  - `ChildBone1`
  - `ChildBone2`
  - `ChildBone3`
  - `ChildBone4`

Vous pouvez également résoudre ce problème en ajoutant des "os terminaux" après chaque `ChildBone`, mais cela nécessite de modifier l'armature.

## Forces

Le type d'intégration définit le type de calcul utilisé pour simuler le mouvement de toute transformation affectée par ce composant. Selon votre choix, les options disponibles dans la section Forces changeront. Vous pouvez choisir entre deux types :

- `Simplified` est une méthode plus stable qui donne une impression de légèreté et est moins réactive aux impulsions et aux forces externes, mais elle est plus facile à configurer.
- `Advanced` est moins stable, mais permet des configurations plus complexes et a tendance à être plus réactive aux impulsions et aux forces externes.
  Avec les paramètres par défaut, ces deux modes sont assez similaires, mais en ajustant les paramètres et en les testant, vous verrez rapidement leurs différences.

> 📘
>
> La plupart (voire tous) des options ci-dessous permettent l'utilisation de courbes en appuyant sur le bouton C à côté du curseur. Les courbes vous permettent d'ajuster la valeur sur toute la chaîne d'os et permettent des configurations TRÈS complexes !
>
> En fait, la plupart des paramètres des PhysBones permettent l'utilisation de courbes ! Apprenez à les utiliser et vos PhysBones seront incroyables !

![physbones-054e326-2022-04-19_11-

32-12_Unity.png](/img/avatars/physbones-054e326-2022-04-19_11-32-12_Unity.png)

`Pull` - Quantité de force utilisée pour ramener les os à leur position de repos.
`Spring` - Quantité de mouvement des os lorsqu'ils tentent de revenir à leur position de repos. Disponible uniquement dans le type d'intégration simplifié.
`Momentum` - Quantité de mouvement des os lorsqu'ils tentent de revenir à leur position de repos. Disponible uniquement dans le type d'intégration avancé. Bien que la description soit la même, l'effet est légèrement différent de celui du ressort.
`Stiffness` - Quantité de mouvement des os pour rester dans leur position de repos. Disponible uniquement dans le type d'intégration avancé.
`Gravity` - Quantité de gravité appliquée aux os. Une valeur positive tire les os vers le bas, une valeur négative les tire vers le haut.
`Gravity Falloff` - Disponible uniquement si la gravité est différente de zéro. Elle contrôle dans quelle mesure la gravité est supprimée lorsque l'os est en position de repos. Une valeur de 1.0 signifie que la gravité n'affectera pas l'os en position de repos. Cela vous permet d'avoir les effets de la gravité lorsque l'os est tourné par rapport à sa position initiale sans affecter l'état de repos de l'os.

Une façon d'utiliser le paramètre "Gravity Falloff" est que si vos cheveux sont modélisés dans la pose souhaitée lorsque vous êtes debout normalement, vous pouvez utiliser un "Gravity Falloff" de 1.0. Ainsi, la gravité ne vous affectera pas lorsque vous êtes simplement debout, et vos cheveux se reposeront dans leur position modélisée. Si vos cheveux sont modélisés à 45 degrés vers l'extérieur et que vous voulez qu'ils soient affectés par la gravité suffisamment pour avoir une belle courbe (mais pas complètement vers l'extérieur ou complètement vers le bas), le curseur vous permet de régler cela et d'utiliser une valeur de 0,5 à 0,8 pour n'avoir qu'une fraction de la gravité en position de repos.

`Immobile Type` modifie le comportement de l'option "Immobile".

Si réglé sur **All Motion**, "Immobile" réduit tout mouvement calculé à partir de la transformation parent de l'os racine. Il s'agit du mode **par défaut** pour les nouveaux PhysBones et les Dynamic Bones convertis. Dans ce mode, tous les mouvements de PhysBone, que ce soit dans l'espace de la scène ou l'espace de jeu, sont atténués par le facteur "Immobile".

Si réglé sur **World (Expérimental)**, "Immobile" annule uniquement le mouvement de translation par rapport à la racine de la scène. Le mouvement via l'animation ou l'IK affecte toujours normalement les os. _Ce mode peut changer à l'avenir !_

Cela signifie que se déplacer dans votre espace de jeu affectera toujours le mouvement de vos PhysBones normalement, mais la locomotion (pousser sur votre joystick pour vous déplacer) aura son mouvement atténué par le facteur "Immobile".

## Limites

La définition des limites vous permet de limiter la quantité de mouvement d'une chaîne d'os PhysBone. Cela est utile lorsque vous ne voulez pas que les cheveux pénètrent dans votre tête et c'est **beaucoup** plus performant qu'un collider !

De plus, lors de la configuration des options des limites, une visualisation de ces limites apparaît dans la vue de la scène lorsque vous avez sélectionné la chaîne d'os PhysBone. Cela peut être extrêmement utile pour affiner les limites !

`Limit Type` a plusieurs modes. Tous permettent d'ajuster la `Rotation` en termes de `Pitch`, `Yaw` et `Roll`, respectivement le long des axes X, Y et Z.

### Aucune

`Aucune` signifie qu'aucune limite n'est activée sur cette chaîne d'os. Il n'y a pas d'options de configuration.

### Angle

`Angle` signifie que la chaîne d'os sera limitée à un `Angle Max`, centré sur un axe défini par `Rotation`. Cela est représenté visuellement comme un cône dans la vue de la scène.

### Charnière

`Charnière` signifie que la chaîne d'os sera limitée à un `Angle Max` le long du plan défini par `Rotation`. Cela est représenté visuellement comme une tranche de cercle, similaire à une part de pizza ou à un morceau de tarte.

### Polaire

`Polaire` est un peu plus complexe. Si vous prenez une `Charnière` et la faites pivoter sur `Yaw

de quelques degrés, vous obtenez un segment de sphère dans les coordonnées `Polaire`. Vous pouvez configurer `Max Pitch` et `Max Yaw` pour ajuster la taille du segment et utiliser `Rotation` pour définir l'emplacement de ce segment sur la sphère. La visualisation de `Polaire` est particulièrement utile.

N'utilisez pas trop souvent les limites polaires, car elles ont un coût de performance non nul. Utiliser un nombre élevé (plus de 64) causera probablement des problèmes. Si vos valeurs de `Max Pitch` et `Max Yaw` sont similaires ou identiques, une limite `Angle` suffira et aura moins d'impact sur les performances.

## Collision

`Rayon` - Rayon de collision autour de chaque os en mètres. Utilisé à la fois pour la collision et la saisie.
`Autoriser la collision` - Autorise la collision avec des colliders autres que ceux spécifiés sur ce composant. Les autres colliders sont actuellement les mains et les doigts de chaque joueur tels que définis par leur avatar.
`Colliders` - Liste des colliders en collision spécifiquement avec ces os.

## Étirement et compression

`Mouvement d'étirement` - Quantité de mouvement qui affectera l'étirement/la compression des os. Une valeur de zéro signifie que les os s'étireront/comprimeront uniquement en raison de la saisie ou des collisions.
`Étirement max` - Quantité maximale d'étirement des os. Cette valeur est un multiple de la longueur initiale des os. [Note : Limites maximales](/avatars/avatar-dynamics/physbones#limites-maximales)
`Compression max` - Quantité maximale de compression des os. Cette valeur est un multiple de la longueur initiale des os.

## Saisie et pose

`Autoriser la saisie` - Autorise les joueurs à saisir les os.
`Autoriser la pose` - Autorise les joueurs à mettre les os en pose après les avoir saisis.
`Mouvement de saisie` - Contrôle le mouvement des os saisis. Une valeur de zéro permet aux os d'utiliser la traction et le ressort pour atteindre la position saisie. Une valeur de un fait que les os se déplacent immédiatement vers la position saisie.
`Aligner sur la main` - Lorsqu'un os est saisi, il sera aligné sur l'os qui le saisit.

## Options

`Paramètre` - Préfixe utilisé pour fournir plusieurs paramètres au contrôleur de l'avatar. Dans les éléments suivants, en définissant le paramètre sur `Queue`, cela remplacerait `{parameter}` par `Queue`.

`{parameter}_EstSaisi`  
 [Bool] Les os sont-ils actuellement saisis ?

`{parameter}_EstPosé`  
 [Bool] Les os sont-ils en pose ?

`{parameter}_Angle`  
 [Float] Plage de 0,0 à 1,0. Angle normalisé de 180 degrés formé entre l'os d'extrémité et sa position de repos d'origine. En d'autres termes, si vous torsadez un os complètement dans la direction opposée à sa direction de départ, ce paramètre aura une valeur de 1,0.

`{parameter}_Étirement`  
 [Float] Plage de 0,0 à 1,0. Proximité des os par rapport à leur longueur maximale d'étirement.

`Est animé` - Permet aux transformations osseuses d'être animées. À chaque image, la position de repos de l'os sera mise à jour en fonction de l'animation appliquée. Cette option doit être activée pour que tous les os de la chaîne PhysBone (y compris l'os racine !) respectent les animations qui leur sont appliquées.

`Réinitialiser lorsqu'il est désactivé` - Lorsque ce composant est désactivé, les os reviennent automatiquement à leur position par défaut.

## Notes importantes, conseils d'utilisation, etc.

**Ne placez pas un composant Constraint et un composant PhysBone sur le même GameObject**, car cela peut causer des problèmes d'ordre d'exécution.

Placez plutôt le Constraint sur l'objet parent. Vous pouvez toujours définir la cible du Constraint sur le GameObject d'origine.

> ❗️ 
> 
> **Les PhysBones ont une limite stricte sur le Meta Quest.** Cela est fait pour éviter une réduction des performances sur les appareils Meta Quest, qui sont souvent déjà faibles en ressources CPU.
> 
> Vous pouvez considérer ces limites comme les limites Très faible pour Quest décrites dans la documentation sur le [Classement minimum des performances affichées](/avatars/avatar-performance-ranking-system#limits-quest).

### Limitations par composant

**Un seul composant PhysBone ne peut pas affecter plus de 256 transformations à la fois.** Cela inclut l'os racine ainsi que tous les enfants. _Cela affecte également les conversions de Dynamic Bones !_

Cependant, vous devriez essayer de ne pas avoir autant de transformations à animer en premier lieu. Essayez de fusionner les os de la chaîne vers leurs parents immédiats. Des outils créés par la communauté comme le plugin Blender de Cat peuvent le faire pour vous.

### Animation des propriétés

Les propriétés des PhysBones telles que Spring, Pull, Stiffness, etc. sont définies à l'initialisation et **ne peuvent pas être animées**.

Cependant, si vous animez une propriété d'un composant PhysBone, puis animez le composant hors et ensuite sur, vous pouvez obtenir le comportement souhaité. Sachez que ce n'est pas une méthode prise en charge pour animer ces propriétés et cela ne sera pas pris en charge dans les futures modifications. (En d'autres termes, cela pourrait ne pas fonctionner. Si cela se produit, nous n'essaierons pas de le réparer.)

### Ossements humains

**Ne définissez pas les ossements humains en tant qu'os racines de PhysBone.** En d'autres termes, ne définissez pas les ossements de la hanche, de la colonne vertébrale, de la poitrine, de la poitrine supérieure, du cou, de la tête ou des membres comme racines. Cela causera des problèmes majeurs.

À la place, dupliquez l'os que vous souhaitez utiliser comme racine et reparentez tous les os enfants que vous souhaitez animer à cette nouvelle racine. Cela doit être fait dans Blender. Des outils créés par la communauté comme le plugin Blender de Cat

peuvent vous aider à effectuer cette opération plus facilement.

### Performance

Les PhysBones sont plus coûteux en termes de performances que les Dynamic Bones, car ils utilisent un système de calcul plus avancé. Veillez à ne pas utiliser un nombre excessif de PhysBones dans votre avatar, car cela pourrait entraîner une diminution des performances, en particulier sur des appareils moins puissants.

### Expérimentation et ajustement

La meilleure façon de comprendre et de maîtriser l'utilisation des PhysBones est de les expérimenter et d'ajuster les paramètres en fonction de vos besoins spécifiques. Essayez différentes configurations, testez les interactions avec d'autres composants de votre avatar et observez les résultats dans la vue de la scène. Avec un peu de pratique, vous pourrez créer des mouvements secondaires réalistes et fluides pour votre avatar.

N'oubliez pas de consulter les ressources de la communauté, les tutoriels et les exemples pour obtenir des conseils supplémentaires sur l'utilisation des PhysBones dans VRChat.