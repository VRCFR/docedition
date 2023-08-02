

Un ID de réseau est l'identifiant utilisé pour déterminer quel objet est lequel en matière de mise en réseau. Dans la plupart des cas, vous n'avez pas besoin de vous en préoccuper, mais cela peut se poser lorsque vous travaillez avec des mondes multiplateformes où les joueurs chargent techniquement deux versions différentes de votre monde.

Les ID de réseau sont le lien entre ces différentes versions, pour s'assurer que tout le monde voit la même chose et que les données sont transmises aux bons objets.

Pour être plus précis, un ID de réseau est simplement un numéro attribué à un GameObject. Par exemple, supposons que vous ayez un ballon de plage avec l'ID 1 et une glace avec l'ID 2. Si ceux-ci sont mélangés, vous pourriez essayer de jouer avec un ballon de plage tandis que quelqu'un d'autre voit que vous jouez avec une glace !

Pour faire face à ces problèmes potentiels et pour vous assurer que vos différentes scènes sont synchronisées, nous avons créé un utilitaire d'ID de réseau.

# Utilitaire d'importation et d'exportation d'ID de réseau

Cet utilitaire vous permet de sauvegarder et de transférer des ID de réseau entre des scènes ou des projets. Vous pouvez le trouver dans l'éditeur Unity, sous `VRChat SDK/Utilitaires/Utilitaire d'importation et d'exportation d'ID de réseau`.
:::note

Vous ne devriez avoir besoin d'utiliser cet utilitaire que si vous développez un monde multiplateforme et que vos différentes versions sont dans des scènes ou des projets différents.
:::

![network-id-utility-9936cee-image1.png](/img/worlds/network-id-utility-9936cee-image1.png)

Lors de l'utilisation de cet outil, vous verrez une liste de tous vos ID de réseau dans l'ensemble de la scène. Si vous ne l'avez pas encore, vous pouvez cliquer sur "Régénérer les ID de scène".
![network-id-utility-05130bf-image4.png](/img/worlds/network-id-utility-05130bf-image4.png)

Lorsque vous êtes prêt à transférer des ID de réseau d'une scène à une autre, cliquez sur le bouton **Exporter** pour enregistrer le fichier quelque part. Ensuite, allez dans l'autre scène, cliquez sur **Importer** et sélectionnez ce fichier.

**Les ID de réseau dans ce format sont enregistrés sous forme de chemin d'accès à l'objet.** Par conséquent, essayez de garder le chemin d'accès de chaque objet identique entre vos scènes. Les autres objets de la scène qui n'ont pas de mise en réseau (comme les maillages) n'ont pas d'importance et peuvent être différents entre vos scènes, tant qu'ils ne sont pas en conflit avec quelque chose qui doit être synchronisé.
![network-id-utility-3b30a4e-image5.png](/img/worlds/network-id-utility-3b30a4e-image5.png)

Si tout correspond entre vos deux scènes, vous devriez voir un gros bloc avec un bouton **Tout accepter**. Cliquez dessus et c'est parti !

# Résoudre les conflits

Il existe plusieurs outils de résolution des conflits dans cet utilitaire.
![network-id-utility-22a9bcf-image3.png](/img/worlds/network-id-utility-22a9bcf-image3.png)

Voici un exemple d'un objet qui existe dans le fichier mais qui n'existe pas dans la scène. Le fichier indique qu'il y a un ID de réseau à ce chemin, mais il ne trouve pas d'objet avec ce chemin. À ce stade, vous pouvez choisir de l'ignorer ou de spécifier un autre objet. Si vous êtes sûr que c'est un objet qui n'a pas besoin d'exister dans cette scène, vous pouvez l'ignorer en toute sécurité. Cependant, s'il s'agit d'un objet qui devrait exister dans votre scène mais qui a simplement un nom différent, vous pouvez le sélectionner. Une fois que vous avez résolu ce conflit, il passera à la section où vous pouvez accepter l'ID de réseau.
![network-id-utility-c5175f8-image2.png](/img/worlds/network-id-utility-c5175f8-image2.png)

Voici un autre exemple où un objet indique qu'il a l'ID de réseau 25, mais le fichier indique qu'un autre chemin devrait avoir 25.

Cela, et de nombreuses autres situations étranges, ne peuvent se produire que si la scène contient des ID de réseau existants avant que vous n'essayiez d'importer un nouveau fichier par-dessus. Si vous copiez des ID entre des scènes, il est très probable que vous voudrez effacer les ID avant d'importer afin de ne pas avoir ce problème. Cependant, ces options existent au cas où vous auriez besoin de faire quelque chose de très spécifique, comme essayer de réparer une scène sans casser certains ID de réseau existants.

Si vous devez résoudre ces conflits, vous pouvez choisir de cliquer sur le bouton "Ignorer tout", ce qui ne touchera pas du tout la scène, ou vous pouvez choisir manuellement celui qui obtient l'ID. Lorsque vous cliquez sur le bouton "Sélectionner", cela résoudra le conflit en appliquant l'ID à l'objet que vous avez sélectionné. Cela peut résoudre un ou plusieurs conflits, donc ne soyez pas surpris si de nombreux conflits disparaissent lorsque vous en résolvez un seul.