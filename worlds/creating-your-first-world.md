

> 🚧 
> 
> Certaines parties de cette page sont en cours de mise à jour.  
> Besoin d'aide ? Rendez-vous sur notre Discord [discord.gg/vrchat](https://discord.gg/vrchat) ou sur notre forum officiel [ask.vrchat.com](https://ask.vrchat.com).

Avant de commencer, assurez-vous d'avoir un projet Unity avec le SDK configuré.

## Étape 1 - Configuration d'une scène

La première chose dont vous avez besoin est une scène. Cela peut être une scène existante avec du contenu ou une nouvelle scène. Une fois la scène ouverte, vous devez faire glisser et déposer le prefab VRCWorld dans votre scène.

Vous pouvez trouver le VRCWorldPrefab en le recherchant dans votre onglet "Projet" et en configurant votre recherche sur "Dans les packages" ou "Tous".

![](/img/worlds/creating-your-first-world-b1946d4-Unity_4t4quWsgTY.png)

## Étape 2 - Création de points d'apparition

Vous devez maintenant configurer au moins un point dans la scène où les utilisateurs peuvent apparaître. Par défaut, les joueurs apparaissent à l'emplacement de votre objet VRCWorld. C'est la configuration la plus simple et celle que la plupart des utilisateurs utilisent.

Si vous souhaitez créer des points d'apparition supplémentaires, créez un GameObject vide et placez-le à l'endroit où vous souhaitez que les utilisateurs apparaissent. Ajoutez le GameObject à la liste "spawns" dans le [VRC_SceneDescriptor](/worlds/components/vrc_scenedescriptor). Faites cela pour autant de points d'apparition que vous le souhaitez.

Si vous avez plus d'un point d'apparition, vous pouvez choisir l'ordre dans lequel les personnes y apparaîtront en modifiant la propriété "Spawn Order".

## Étape 3 - Paramètres du descripteur

Il existe différentes options que vous pouvez configurer dans le [VRC_SceneDescriptor](/worlds/components/vrc_scenedescriptor) pour modifier le comportement de la salle. Voici quelques-unes des plus importantes.

_Spawns_ - Un tableau de transformations où les joueurs apparaîtront lorsqu'ils rejoindront votre monde. Par défaut, les joueurs apparaissent à la transformation de votre descripteur de scène.

_Respawn Height_ - Hauteur-Y à laquelle les joueurs réapparaissent et les objets apparaissent ou sont détruits. Tout ce qui se trouve en dessous de ce niveau Y sera réapparu (ou détruit, dans le cas d'objets configurés).

_Reference Camera_ - Une caméra sur laquelle vous pouvez appliquer des paramètres qui sont appliqués au joueur lorsqu'il rejoint la salle. Souvent utilisée pour ajuster les plans de découpage et ajouter des effets de post-traitement.

Vous pouvez trouver d'autres paramètres sur la page [VRC_SceneDescriptor](/worlds/components/vrc_scenedescriptor).

## Étape 4 - Configuration de la scène

Commençons ! Allez dans `VRChat SDK > Afficher le panneau de contrôle > Builder`. Là, vous verrez des éléments facultatifs que vous pouvez configurer dans votre scène, ainsi que des options pour construire votre monde. Suivez ces opérations :

- Configuration des calques pour correspondre aux calques de VRChat. Vous devriez absolument le faire, sinon votre monde risque de ne pas fonctionner correctement.
- Configuration de la matrice de collision des calques pour correspondre à celle de VRChat. Voir ci-dessus. Ne sautez pas cette étape !
- Appliquer la spatialisation 3D aux AudioSources 3D automatiquement à l'exécution. Utilisez cette option si toutes les AudioSources de votre scène doivent être spatialisées.
- Appliquer la spatialisation 3D aux AudioSources 3D de la scène actuelle. Utilisez cette option si vous souhaitez ajouter ultérieurement des AudioSources 2D, comme de la musique d'ambiance.

## Étape 5 - Construction de votre monde

Ensuite, vous devez construire votre monde ! Vous devrez choisir ce que vous ferez en premier : vous pouvez soit créer une version de test pour tester votre monde sans le télécharger, soit publier votre monde directement sur VRChat. Sous les rubriques "Test" et "Publish", vous trouverez les boutons "Last Build" et "New Build". "Last Build" permet de charger la dernière version de test ou de téléchargement du monde. "New Build" permet de créer un nouveau monde pour un test ou un téléchargement.

_(Optionnel)_  
Si vous souhaitez tester votre monde, appuyez sur le bouton "New Build" sous la rubrique "Test". Cela créera une nouvelle version de votre monde et le lancera dans VRChat. L'option "Number of Clients" est utilisée lorsque vous souhaitez ouvrir plusieurs clients pour tester le comportement en réseau.

Maintenant, nous pouvons construire et télécharger votre monde en appuyant sur le bouton "New Build" situé sous la rubrique "Publish" ! Cela construira votre monde et le préparera pour le téléchargement. Unity devrait passer en mode lecture et afficher une fenêtre dans laquelle vous pouvez entrer des détails sur le téléchargement, y compris :

- Nom du monde - Le nom de votre monde, tel qu'il est affiché à tout le monde !
- _(Bientôt disponible)_ Capacité recommandée - Le nombre maximum de joueurs recommandé pour votre monde.
  - Si une instance publique atteint sa capacité recommandée, VRChat découragera les joueurs de rejoindre. L'instance ne figurera plus dans la liste des instances publiques de VRChat.
  - Les joueurs peuvent toujours essayer de rejoindre l'instance dans certaines circonstances s'ils ont une URL d'invitation directe sur vrchat.com.
- Capacité des joueurs - Le nombre maximum de joueurs autorisés dans votre monde.
  - Si une instance atteint sa capacité de joueurs, les nouveaux joueurs ne peuvent pas rejoindre.
  - Le créateur de l'instance, le créateur du monde ou le propriétaire du groupe peuvent toujours rejoindre, même si cela dépasse la capacité de joueurs. (Sauf s'ils n'ont pas la permission d'entrer/voir cette instance)

> 🤔 Que se passe-t-il si mon monde n'a pas de "capacité recommandée" ?
> 
> Si vous avez téléchargé votre monde VRChat sans "capacité recommandée", la capacité des joueurs fonctionne différemment :
> 
> - "Capacité recommandée" sera identique à la valeur de votre capacité des joueurs
> - "Capacité des joueurs" sera **deux fois** la valeur de votre capacité des joueurs
> 
> Par exemple : si vous définissez la "capacité des joueurs" à 10 et que vous n'avez pas défini de "capacité recommandée", votre "capacité des joueurs" _réelle_ sera de 20. La "capacité des joueurs" était parfois appelée "la limite souple" pour cette raison.

- Description - Celle-ci s'affichera sur la page "Détails du monde" dans VRChat et sur le site web.
- Avertissements de contenu - **Les avertissements de contenu sont obsolètes et ne sont pas utilisés actuellement.** Vous ne pouvez pas télécharger de contenu sur VRChat qui viole nos [lignes directrices communautaires](https://vrchat.com/community-guidelines) ou nos [conditions d'utilisation](https://vrchat.com/legal). Le non-respect de cette règle (même si vous avez coché un avertissement de contenu) entraînera des mesures de modération.

Vous pouvez également retourner dans la vue de la scène et ajuster la caméra VRCCam afin que la miniature soit parfaite.

Une fois toutes ces informations saisies, vous devez confirmer que vous avez le droit de télécharger le contenu sur VRChat. Une fois que vous l'avez fait, vous pouvez cliquer sur le bouton "Télécharger". La salle sera alors téléchargée sur VRChat ! Lorsque c'est terminé, vous devriez pouvoir le voir dans le jeu ou via le gestionnaire de contenu dans le SDK via `VRChat SDK > Afficher le panneau de contrôle > Gestionnaire de contenu`.

> 🚧 Échecs de téléchargement
> 
> Si votre monde ne parvient pas à se télécharger, vérifiez la console pour voir s'il y a des erreurs, si c'est le cas, résolvez-les avant de tenter de reconstruire votre monde. Consultez nos autres documentations ou demandez de l'aide sur [Discord](https://discord.com/invite/vrchat) si vous avez besoin d'aide.