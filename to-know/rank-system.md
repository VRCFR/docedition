

:::caution[Mise à jour en attente]
Cette section est en attente de mises à jour ! Les noms des avatars et le système de sécurité de VRChat ont récemment changé, donc les captures d'écran peuvent ne pas être exactes. Cependant, la fonctionnalité reste la même.
:::

![](https://files.readme.io/894b94a-MediumHeader_v4_Friends.png "MediumHeader_v4_Friends.png")

Le système de Confiance et de Sécurité de VRChat est une nouvelle extension du système de Confiance VRChat actuellement mis en œuvre. Il est conçu pour protéger les utilisateurs contre les utilisateurs nuisibles qui utilisent des shaders d'espace d'écran, des sons ou des microphones bruyants, des effets de particules visuellement perturbants ou malveillants, et d'autres méthodes que quelqu'un pourrait utiliser pour perturber votre expérience dans VRChat.

Ce système est conçu pour **rendre le contrôle à l'utilisateur**, permettant aux utilisateurs de déterminer où, quand et comment ils voient différentes caractéristiques d'avatar qui peuvent être distrayantes ou malveillantes si elles sont utilisées de manière inappropriée.

Il est important de noter que ce système est actuellement en **BÊTA**, et qu'il peut changer à chaque mise à jour ou patch.

<iframe src='https://gfycat.com/ifr/LinearInfantileAmericancrayfish' frameborder='0' scrolling='no' allowfullscreen width='600' height='453'></iframe>

Le système de Confiance et de Sécurité est conçu de telle sorte que, même en laissant les paramètres par défaut, le système s'assure que quelqu'un ne peut pas vous attaquer avec des caractéristiques d'avatar malveillantes. Les utilisateurs malveillants ne verront pas ces caractéristiques, vous permettant ainsi de vivre une bonne expérience dans le métaverse.

Ce système se compose de deux composants essentiels : le système de Confiance et le système de Sécurité. Explorons-les un peu plus en détail.

### Le système de Confiance

Le système de Confiance est déjà implémenté dans VRChat ! Il détermine quand un utilisateur est autorisé à télécharger du contenu - vous avez peut-être entendu parler de nous l'appelant "Content Gating" auparavant. Cependant, le système va bien au-delà de la simple détermination si vous pouvez télécharger du contenu - il examine le comportement de l'utilisateur pour déterminer la "Confiance", qui est un agrégat de nombreuses variables. Nous pouvons facilement ajuster la manière dont nous calculons cette valeur, donc nous pouvons la régler au fur et à mesure que le temps passe.

#### Rang de Confiance

La Confiance d'un utilisateur contribue à ce que nous avons appelé un "Rang de Confiance", qui indique le temps qu'un utilisateur a passé dans VRChat, la quantité de contenu qu'il a contribué, les amis qu'il a faits, et de nombreux autres facteurs. Ces rangs sont les suivants :

![](https://files.readme.io/c8af264-TrustLevels_4.png "TrustLevels_4.png")

Vous gagnez ces rangs simplement en jouant à VRChat - en explorant des mondes, en vous faisant des amis et en créant du contenu, vous gagnerez plus de Confiance, ce qui déterminera votre Rang de Confiance.

Les rangs sont affichés sur les plaques nominatives lorsque vous ouvrez votre menu rapide. Sinon, ils se dérobent et ne sont pas visibles pendant la lecture normale.

Les **Amis** sont un Rang de Confiance spécial. Les utilisateurs que vous avez ajoutés en tant qu'Amis verront toutes leurs caractéristiques d'avatar affichées au niveau du Bouclier Normal, et vous pouvez les personnaliser comme n'importe quel autre Rang de Confiance.

La transition entre "Visiteur" et "Nouvel Utilisateur" est spéciale - lorsque qu'un Visiteur devient un Nouvel Utilisateur, il acquiert la possibilité de télécharger du contenu sur VRChat tant qu'il utilise un compte VRChat. Les utilisateurs reçoivent une notification lorsqu'ils atteignent ce rang et sont dirigés vers la page de documentation de VRChat pour commencer à créer du contenu.

Dans une version future, les utilisateurs recevront une notification lorsqu'ils passent d'un Rang de Confiance à un autre.

Tous les rangs de "Utilisateur Connu" et au-delà ont également la possibilité de désactiver l'affichage de leur rang sur leur plaque nominative. Ils peuvent choisir d'apparaître en tant qu' "Utilisateur", ce qui changera la couleur de leur plaque nominative, et **modifiera également le comportement du système de Sécurité pour correspondre au modèle d'Utilisateur**. Cela concerne les utilisateurs qui ne souhaitent pas afficher leur rang élevé pour quelque raison que ce soit.

Par défaut, les utilisateurs "Connu" et "Digne de Confiance" afficheront leur rang. L'utilisation du bouton de bascule vous ramènera au rang "Utilisateur".

![](https://files.readme.io/b89003f-ShowTrustRank_v3_toggle_wm.png "ShowTrustRank_v3_toggle_wm.png")

En outre, il existe un rang spécial appelé "Ennui". Ces utilisateurs ont causé des problèmes aux autres, et auront un indicateur au-dessus de leur plaque nominative lorsque votre menu rapide est ouvert. La plupart du temps, les avatars de ces utilisateurs seront complètement bloqués. Vous ne les verrez probablement pas souvent - ce qui est une bonne chose !

Enfin, il existe un rang "Équipe VRChat", qui n'est utilisable que par les membres de l'équipe VRChat. Lorsqu'un membre de l'équipe VRChat a son tag "DEV" activé, vous verrez ce rang dans le menu rapide lorsque vous les sélectionnez. Si vous doutez qu'un utilisateur avec une étiquette "DEV" appartienne réellement à l'équipe VRChat, il vous suffit d'ouvrir votre menu rapide, de les sélectionner et de vérifier leur Rang de Confiance. S'il ne dit pas "Équipe VRChat" sous la miniature de l'avatar, alors cet utilisateur n'est pas membre de l'équipe VRChat et essaie probablement de tromper les utilisateurs. N'hésitez pas à prendre une capture d'écran et à les signaler à l'équipe de Modération !

Si un membre de l'équipe VRChat n'a pas son tag "DEV" activé, il apparaîtra comme un utilisateur normal.

### Que fait le

 système de Sécurité ?

"**Sécurité**" est un nouvel onglet de menu qui vous permet de configurer la manière dont les utilisateurs de chaque rang sont traités en ce qui concerne leur affichage dans VRChat. Cela affecte de nombreux aspects de la présence d'un utilisateur dans VRChat :

- **Voix** — Met en sourdine ou réactive le microphone de l'utilisateur (chat vocal)
- **Avatar** — Cache ou montre l'avatar de l'utilisateur ainsi que toutes ses caractéristiques d'avatar. Lorsqu'un avatar est masqué, il affiche un avatar "muet".
- **Icône de l'utilisateur** — Contrôle la visibilité de l'icône de l'utilisateur pour ce Rang de Confiance. Lorsqu'une icône est masquée, elle est "censurée" avec un effet de mosaïque.
- **Audio de l'Avatar** — Active ou désactive les effets sonores de l'avatar de l'utilisateur (hors microphone)
- **Animations** — Active ou désactive les animations personnalisées sur l'avatar de l'utilisateur
- **Shaders** — Lorsqu'il est désactivé, tous les shaders sur l'avatar de l'utilisateur sont ramenés à "Standard". Le comportement derrière le système de blocage des shaders est détaillé sur notre page de documentation [Système de Remplacement des Shaders](doc:shader-fallback-system) 
- **Particules et Lumières** — Active ou désactive les systèmes de particules de l'avatar de l'utilisateur, ainsi que toutes les sources lumineuses. Cela bloquera également les composants "Line" et "Trail Renderer".

Chaque rang possède ses propres paramètres uniques. Pour illustrer cela, voici une capture d'écran du Menu de Sécurité :

![](https://files.readme.io/3b64fe0-SafetyShield_Friends_Custom.png "SafetyShield_Friends_Custom.png")

Il y a **quatre éléments principaux** dans ce Menu auxquels il convient de prêter attention.

![](https://files.readme.io/8e617e2-ShieldLevelsBar.png "ShieldLevelsBar.png")

En haut se trouve **une rangée de "Niveaux de Bouclier"**, qui sont des paramètres prédéfinis pour le système de Sécurité que nous avons développés. Ces Niveaux devraient couvrir la plupart de vos besoins - cependant, vous êtes libre de les personnaliser complètement dans le Niveau "Personnalisé", qui est un mode spécial où vous pouvez créer vos propres paramètres.

![](https://files.readme.io/fc1f584-AvatarFeaturesBar.png "AvatarFeaturesBar.png")

Au milieu se trouvent les **paramètres réels pour le Niveau de Bouclier que vous avez sélectionné**. Ils couvrent chacun des éléments que le système de Sécurité affecte, et si vous êtes en mode personnalisé, vous pouvez les activer ou les désactiver comme bon vous semble.

![](https://files.readme.io/85fab11-TrustRanksBar.png "TrustRanksBar.png")

En bas se trouve **une liste de chacun des Rangs de Confiance**. Lorsque vous avez choisi un "Mode de Sécurité", vous pouvez sélectionner chaque Rang pour voir comment les caractéristiques de l'avatar de ce Rang sont configurées.

![](https://files.readme.io/a665bd0-Tooltips.png "Tooltips.png")

Le **texte à l'intérieur de la zone bleue** en dessous des Modes de Sécurité change lorsque vous sélectionnez différents Modes. Le **texte en bas** change également lorsque vous explorez le menu, et vous informe sur l'élément de l'interface utilisateur sur lequel vous pointez.

Une fois que vous avez terminé de configurer cela, fermez le menu. Les paramètres seront appliqués, et vous les verrez prendre effet sur les utilisateurs autour de vous.

En général, nous avons réglé le système de manière à ce que la plupart des utilisateurs puissent laisser le système en mode "Normal". La plupart des utilisateurs ne devraient pas avoir à faire quoi que ce soit, et le système de Sécurité fonctionnera correctement. Si vous souhaitez **personnaliser la Sécurité à votre guise**, vous êtes libre de le faire via le **Niveau de Bouclier Personnalisé**.

<iframe src='https://gfycat.com/ifr/MajesticAdmirableIsopod' frameborder='0' scrolling='no' allowfullscreen width='600' height='453'></iframe>

Vous pouvez **réinitialiser les paramètres personnalisés** que vous avez définis en cliquant sur "**Réinitialiser les paramètres personnalisés**" en haut à droite du menu.

<iframe src='https://gfycat.com/ifr/MilkyHoarseGermanpinscher' frameborder='0' scrolling='no' allowfullscreen width='600' height='453'></iframe>

Enfin, vous remarquerez peut-être que les paramètres pour le "Mode Sûr" dans le système ont disparu. C'est parce qu'ils ont été intégrés au système de Sécurité. En utilisant le raccourci clavier pour le "Mode Sûr" (Shift+Esc sur Bureau, les deux gâchettes + les deux boutons de menu en VR), vous passerez en mode "Niveau de Bouclier Personnalisé" et toutes les fonctions seront désactivées pour tous les rangs. Nous sommes conscients que ce comportement réinitialisera vos paramètres personnalisés, et nous prévoyons de mettre en place un "Niveau Sûr" dédié dans une future mise à jour.

#### Masquer ou afficher des utilisateurs spécifiques

Vous pouvez rencontrer un utilisateur qui, malgré son rang élevé, porte un avatar que vous préférez ne pas voir. Vous pouvez **sélectionner cet utilisateur et choisir "Masquer l'Avatar"** dans son panneau social. Cela masquera l'avatar de cet utilisateur et désactivera toutes les caractéristiques sauf la voix. Vous pouvez réactiver leur avatar et leurs caractéristiques en cliquant simplement à nouveau sur le bouton, qui sera alors libellé "Afficher l'Avatar".

Si vous souhaitez que le système de Sécurité reprenne le contrôle de l'affichage de l'avatar, il vous suffit de cliquer sur "Utiliser les paramètres de Sécurité".

**Vous pouvez désactiver tout le système si vous le souhaitez.** En sélectionnant le Niveau de Bouclier "Aucun", presque toutes les caracté

ristiques seront affichées pour chaque rang, ou créez un Niveau de Bouclier Personnalisé avec toutes les caractéristiques activées pour tous les rangs. Cependant, nous ne recommandons pas d'utiliser ce paramètre à moins que vous n'ayez confiance en tout le monde dans la salle. Cela n'affecte pas les utilisateurs Nuisibles - leurs caractéristiques seront toujours masquées à moins que vous ne les affichiez explicitement.

**Vous pouvez outrepasser ces paramètres individuellement pour chaque utilisateur** de deux manières. La première consiste à sélectionner un utilisateur dont l'avatar ou les caractéristiques sont masqués par les paramètres actuels de Sécurité, trouver "Afficher l'Avatar" et cliquer dessus. Cela affichera l'avatar et toutes les caractéristiques, quel que soit le mode de Sécurité que vous avez actuellement activé. "Masquer l'Avatar" fait l'inverse - quel que soit le mode de Sécurité sur lequel vous êtes, l'avatar de cet utilisateur sera masqué. Vous pouvez choisir "Utiliser les paramètres de Sécurité" pour que le mode de Sécurité que vous utilisez gère la visibilité de l'avatar de cet utilisateur.

La deuxième manière consiste à se faire des amis ! **Les Amis n'ont aucune caractéristique masquée dans le Niveau de Bouclier Normal**. Si vous avez quelqu'un en ami, nous supposons que vous avez implicitement confiance en lui. Ainsi, les caractéristiques de leur avatar seront complètement activées dans le Niveau de Bouclier Normal. Si, pour une raison quelconque, vous souhaitez masquer l'avatar de votre ami, vous pouvez toujours le faire avec le bouton "Masquer l'Avatar".

### Mode Sûr

Selon les [commandes](doc:controls) que vous utilisez, il existe un raccourci pour désactiver immédiatement toutes les fonctions pour tous les utilisateurs autour de vous. Cela s'appelle le "Mode Sûr".

Sur les contrôleurs VR, tirer les deux gâchettes et appuyer sur les deux boutons de menu activera ce mode. Sur le Bureau, appuyer sur Shift et Échap activera ce mode.

Lorsqu'il est activé, le système de Sécurité passe en mode "Niveau de Bouclier Personnalisé" avec toutes les fonctions désactivées pour tous les utilisateurs. Un texte apparaîtra au milieu de l'écran expliquant ce qui vient de se passer. **Cela remplacera vos paramètres personnalisés, si vous les utilisiez auparavant.** Tous les avatars de tous les utilisateurs seront masqués et toutes les voix seront désactivées chez les autres utilisateurs.

Pour désactiver le Mode Sûr, réglez votre système de Sécurité sur votre mode précédent. Si vous utilisiez le mode personnalisé, vous devrez réinitialiser manuellement vos paramètres précédents.

### "Mode de Numérisation" du Menu Rapide

Lorsque vous ouvrez votre Menu Rapide, vous pourrez voir plus d'informations sur les plaques nominatives des utilisateurs, ainsi que des informations sur ces derniers. Cela agit comme un "scanner", fournissant plus d'informations lorsque votre Menu Rapide est ouvert. Si vous pointez vers un utilisateur, vous obtiendrez des informations rapides de base. En cliquant sur l'utilisateur, vous verrez plus de détails. Cela affichera leur miniature d'avatar, leur nom, leur rang affiché, ainsi que d'autres informations.

#### Interagir avec un utilisateur

![](https://files.readme.io/5793abc-1_oxRPBqCLG-oKruMr7XJJyQ.png "1_oxRPBqCLG-oKruMr7XJJyQ.png")

Comme vous pouvez le voir en haut à gauche, l'image de l'avatar et le nom de l'utilisateur sont affichés. Leur Rang de Confiance est affiché sous la miniature de l'avatar, et la miniature est mise en évidence dans la couleur appropriée . À droite, vous pouvez voir leur statut actuel. La boîte de texte sous le statut est une "infobulle", qui vous donnera des informations utiles en fonction de ce que vous pointez du doigt.

Sélectionner un utilisateur ouvre un menu social plus détaillé.

![](https://files.readme.io/a89a564-QM_UserActions_1.png "QM_UserActions (1).png")

En utilisant ce menu, vous pouvez également envoyer une demande d'ami à l'utilisateur, activer ou désactiver sa voix, et consulter les détails sur l'utilisateur (ce qui ouvre le menu social complet pour cet utilisateur). En cliquant sur le bouton "Non Bloqué"/"Bloqué", vous pouvez bloquer ou débloquer cet utilisateur.

En cliquant sur "Précédent" et "Suivant" en haut, vous pouvez faire défiler tous les utilisateurs dans l'instance. C'est utile pour avoir une idée de la manière dont vous avez configuré les paramètres pour les utilisateurs, qui vous avez mis en sourdine, qui vous avez en ami, etc.

Les boutons "Avertir" et "Expulser" sont disponibles lorsque vous êtes le propriétaire d'une instance - cela vous permet de modérer votre instance selon vos souhaits. Le bouton "Retour" vous ramènera au menu précédent, qui est probablement le Menu Rapide.

#### Masquer et afficher des avatars

Dans le Menu Rapide social, cliquer sur "Utiliser les paramètres de Sécurité" permettra au Mode de Sécurité que vous avez choisi de déterminer comment afficher l'avatar de cet utilisateur. Le choix de "Afficher l'Avatar" ou "Masquer l'Avatar" remplacera le Mode de Sécurité que vous avez activé, et affichera/masquera l'avatar et toutes ses caractéristiques.

Cliquer sur "Afficher l'Avatar" est le **moyen le plus simple** de remplacer le

 Mode de Sécurité que vous avez activé, car il réactivera toutes les caractéristiques de l'avatar de cet utilisateur. En cliquant sur "Masquer l'Avatar", vous activerez un mode personnalisé où vous contrôlerez l'affichage de l'avatar de cet utilisateur. **Si vous êtes en "Niveau de Bouclier Personnalisé", cela remplacera également tous vos paramètres pour ce niveau.**

#### Niveaux de Confiance et de Sécurité

Le menu des paramètres de Sécurité vous permettra de configurer les Niveaux de Bouclier en fonction des rangs de confiance. Les Niveaux de Bouclier déterminent comment les utilisateurs de chaque rang sont traités en ce qui concerne leur affichage dans VRChat, en particulier leurs caractéristiques d'avatar.

### Conclusion

En bref, le système de Confiance et de Sécurité de VRChat est conçu pour permettre aux utilisateurs de mieux contrôler leur expérience dans le métaverse. Vous pouvez ajuster les paramètres pour chaque rang de confiance en fonction de vos préférences personnelles. Le système permet de protéger les utilisateurs contre les abus et de s'assurer qu'ils peuvent profiter de leur temps dans VRChat en toute sécurité.