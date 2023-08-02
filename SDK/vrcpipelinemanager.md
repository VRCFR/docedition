

Utilisé pour stocker l'identifiant d'un monde ou d'un avatar.
:::note Ajouté automatiquement

Ce composant est ajouté automatiquement lorsque le composant dont il dépend est ajouté à un objet. Vous ne devriez pas avoir besoin d'ajouter ce composant manuellement.
:::

| Paramètre     | Description                            |
|--------------|---------------------------------------|
| ID de Blueprint | L'identifiant unique de l'avatar ou du monde |

Si vous souhaitez télécharger le monde ou l'avatar sur un autre blueprint, vous pouvez appuyer sur le bouton `Détacher (optionnel)`
:::danger Format de blueprint requis

Les identifiants de blueprint ne peuvent être que dans le format suivant, où 0 est remplacé par [0-9] [a-f]:

`avtr_00000000-0000-0000-0000-000000000000`

`wrld_00000000-0000-0000-0000-000000000000`

Tout autre format d'ID ne sera pas accepté. Cela se fait normalement automatiquement, vous ne devriez donc jamais avoir à créer votre propre ID de Blueprint - cliquez simplement sur "Attacher" et un ID sera généré pour vous.
:::

![vrcpipelinemanager-7d57e76-Unity_2017-12-10_01-35-44.png](/img/sdk/vrcpipelinemanager-7d57e76-Unity_2017-12-10_01-35-44.png)

Si vous avez un ID de blueprint que vous souhaitez télécharger, vous pouvez en attacher un nouveau avec le bouton "Attacher (optionnel)"

![vrcpipelinemanager-db63e77-Unity_2017-12-10_01-37-47.png](/img/sdk/vrcpipelinemanager-db63e77-Unity_2017-12-10_01-37-47.png)

:::caution ASTUCE

N'ayez pas plus d'un PipelineManager dans la scène lors de la construction d'un monde ! Vous risquez de télécharger vers le mauvais ID de blueprint.

:::