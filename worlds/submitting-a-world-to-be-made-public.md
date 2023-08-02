

Vous voulez rendre votre monde public ? Vous êtes au bon endroit ! Vous devez soumettre votre monde aux **Community Labs**.

Avant de soumettre votre monde aux Community Labs, il y a quelques choses que vous devriez prendre en compte. **Assurez-vous de tout lire !** Ne pas le faire pourrait entraîner le retrait de votre monde, ou qu'il reste à jamais dans les Community Labs.

Vous pouvez soumettre votre monde aux Community Labs sur VRChat.com (Modifier les infos du monde -> Zone de danger -> Visibilité du monde -> Publier) ou chaque fois que vous téléchargez une nouvelle version dans Unity.

La publication de votre monde le rendra immédiatement disponible pour tous les utilisateurs qui ont opté pour les Community Labs. À terme, votre monde deviendra public et accessible à tous les utilisateurs en dehors des Community Labs ! [En savoir plus sur les Labs ici.](https://docs.vrchat.com/docs/vrchat-community-labs)

## Informations importantes

- **Vous ne pouvez soumettre qu'un seul monde par utilisateur tous les sept jours aux Community Labs.**
- **Vous pouvez mettre à jour votre monde autant de fois que vous le souhaitez.** Il vous suffit d'envoyer une mise à jour ! Cela n'affectera pas le statut de votre monde.
- **Si votre monde est déjà public, vous n'avez pas besoin de le soumettre à nouveau en cas de mise à jour.** Il sera mis à jour automatiquement et vous ne perdrez pas votre statut public.
- Si votre monde ou tout contenu présent dans le monde (vidéos, avatars, images) viole les Conditions d'utilisation de VRChat ou les Directives de la communauté, votre capacité à soumettre des mondes aux Community Labs sera suspendue pendant une certaine période. Des suspensions répétées peuvent entraîner des actions de modération in-app.
- **Les avertissements de contenu sont obsolètes et ne sont pas utilisés pour le moment.** Vous ne pouvez pas télécharger de contenu sur VRChat qui viole nos [Directives de la communauté](https://vrchat.com/community-guidelines) ou nos [Conditions d'utilisation](https://vrchat.com/legal). Le faire (même si vous avez coché un avertissement de contenu) entraînera des actions de modération.
- Nous n'approuvons pas les mondes via les DM Discord, les e-mails à VRChat ou tout autre canal.
- Si votre monde est _très volumineux_, nous pouvons vous demander de réduire la taille du monde et de le retirer de la version publique en attendant. **Essayez de garder vos mondes en dessous de 200 Mo.**

## Mondes d'avatars / Toutes les statues d'avatars dans n'importe quel monde

- **Les avatars sur les statues doivent être "raisonnablement optimisés".** Consultez notre documentation sur l'[Optimisation des avatars](/avatars/avatar-optimizing-tips) pour plus de détails.
  Évitez de partager des avatars de très mauvaise qualité. Cela s'applique à tous les mondes, pas seulement aux mondes d'avatars. Si les avatars de votre monde ont des problèmes de performances graves, votre monde peut être retiré de la version publique ou des Community Labs.
- **Si vous téléchargez un monde avec des avatars temporaires et que vous les remplacez par des avatars qui violent les Conditions d'utilisation, après avoir rendu votre monde public, vous serez suspendu pour un mois pour soumettre des mondes. Selon la gravité de l'infraction, vous pourriez faire l'objet d'une modération in-app.**
- **Si vous avez un monde d'avatars, aucun de vos avatars ne doit violer les Conditions d'utilisation / Directives de la communauté.**
- Renseignez-vous sur l'utilisation des plugins [Cat's Blender](https://github.com/absolute-quantum/cats-blender-plugin) et du complément Texture Combiner de Shotariya pour Blender afin d'optimiser vos modèles.

## Conseils de performance

- **Visez au moins 45 FPS avec un seul utilisateur VR au point de spawn.** Si vous n'avez pas de casque VR, demandez à un ami de tester le monde pour vous. Un monde qui fonctionne mal signifie que les gens ne passeront pas de temps dans votre monde, et il sera difficile de sortir des Labs.
- **N'utilisez pas de shaders qui ne sont pas compatibles avec la VR.** Les shaders doivent prendre en charge le rendu stéréo à passage unique. Si vous recherchez un bon shader d'eau, [consultez le shader d'eau claire de Silent](https://gitlab.com/s-ilent/clear-water).
- **Utilisez des shaders mobiles sur Android.** La plupart des shaders fonctionneront sur Android, mais ils nécessitent généralement plus de puissance de traitement pour être rendus. Utilisez des shaders mobiles si possible.
- **Faites très attention aux effets de post-traitement.** Certains effets de post-traitement basés sur l'espace de l'écran peuvent causer des problèmes majeurs pour les utilisateurs de la VR. Soyez particulièrement prudent avec l'aberration chromatique, la réflexion basée sur l'espace de l'écran et l'occlusion ambiante basée sur l'espace de l'écran.
- **Des problèmes surviennent lorsque vous placez plus de 2 lecteurs vidéo dans une pièce.** Cela a généralement un impact négatif sur les performances.
- **Des problèmes surviennent également lorsque vous placez plus d'un miroir dans votre pièce.** Les miroirs affectent gravement les performances d'un monde. Si vous avez un miroir dans la pièce, assurez-vous de le mettre en activé/désactivé.
- **Nous vous RECOMMANDONS FORTEMENT de ne pas activer les miroirs par défaut.** Ajoutez un commutateur qui peut être activé par les joueurs ou activé automatiquement lorsque les joueurs entrent dans une certaine zone.
- **N'utilisez PAS trop de lumières en temps réel.** Elles sont **très** coûteuses et peuvent nuire aux performances de votre monde si elles sont mal utilisées.
- **Le Baking de votre éclairage est extrêmement important et peut vous procurer d'énormes gains de performances.**

## Conseils généraux

- Testez votre monde ! Il n'est pas rare que nous voyions des mondes où vous tombez immédiatement hors de la porte.
- Testez votre monde en VR également. Vérifiez que vos shaders fonctionnent correctement et s'affichent correctement en VR. Si vous n'avez pas de casque VR, demandez à un ami de jeter un coup d'œil autour de lui.
- **_TESTEZ VOTRE ÉCLAIRAGE !_** L'éclairage d'un monde est très important, et le faire correctement est essentiel. Ne testez pas simplement avec des shaders Toon, car ils ne représentent pas correctement l'éclairage. Utilisez un shader standard ou PBR pour voir comment l'éclairage l'affecte. Si vous êtes surexposé, vous avez probablement trop de lumières, votre intensité est trop élevée ou vous devez envisager d'utiliser le mappage des tons.
- Vous voulez rendre votre monde privé à nouveau ? Modifiez votre monde sur le site web et vous pouvez le rendre privé.
- Évitez d'utiliser directement des fichiers `.blend`. Exporter des fichiers FBX à partir de Blender pour les utiliser dans VRChat cause généralement moins de problèmes.

Si vous avez des questions sur le processus, [visitez notre forum](https://ask.vrchat.com/c/worlds/27) ou envoyez un e-mail à hello@vrchat.com avec votre question. Si vous organisez un événement ou avez un monde très fréquenté dans l'application et avez besoin qu'un monde soit rendu public à un moment différent, veuillez nous contacter par e-mail au moins 48 heures à l'avance.

## Soumission aux Community Labs

Une fois que vous avez tout lu ci-dessus, soumettez votre nouveau monde aux Community Labs ! Si vous vous demandez comment fonctionnent les Community Labs, consultez notre documentation sur les [Community Labs de VRChat](https://docs.vrchat.com/docs/vrchat-community-labs).

## Devenir un monde de jeu ou un monde d'avatars

Si vous voulez que votre monde soit catégorisé comme un monde d'avatars ou un monde de jeu, ajoutez simplement la balise appropriée lors du téléchargement.

> 🚧 Ne pas abuser des lignes de monde
>
> Ces règles sont en place pour donner à **tous** les mondes une chance d'être découverts. L'utilisation de techniques "SEO-like" n'est pas autorisée et entraînera des actions telles que la suppression des balises, ou dans des cas répétés/graves, une modération de l'auteur.
>
> VRChat se réserve le droit d'agir sur les utilisateurs qui abusent de nos systèmes pour promouvoir leur contenu de manière injuste ou trompeuse.

### Mondes d'avatars

**Un monde d'avatars est un monde où l'obtention et le partage d'avatars sont** **_le principal objectif._** Trouver un avatar dans des mondes étiquetés comme mondes d'avatars devrait être rapide et facile, et ne devrait pas être une réflexion après coup ou une "ajout" à une autre fonctionnalité clairement principale du monde.

Pour catégoriser votre monde comme un monde d'avatars, ajoutez le tag `avatar`.

### Mondes de jeu

**Un monde de jeu est un monde où jouer à un jeu ou à un ensemble de jeux est** **