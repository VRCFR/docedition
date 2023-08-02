

Trouvez plus d'informations sur les composants limités sur notre page [Optimisation du contenu des quêtes](/platforms/android/quest-content-optimization)."

Cette page décrira les différentes limitations en place pour la version Oculus Quest de VRChat. Ces limitations sont en place dans l'intérêt des performances, de la sécurité des utilisateurs et pour décourager les comportements malveillants.

Trouvez plus d'informations sur les composants limités sur notre page [Optimisation du contenu des quêtes](/platforms/android/quest-content-optimization).

# Limitations spécifiques aux avatars
Bien que la version actuelle de VRChat n'implémente pas de limite stricte, **nous pourrions implémenter une limite stricte pour les avatars basée sur le nombre de triangles, le nombre de matériaux, le nombre de maillages et d'autres caractéristiques à l'avenir.** Veuillez garder à l'esprit nos recommandations telles que décrites dans [Optimisation du contenu des quêtes](/platforms/android/quest-content-optimization).

Actuellement, si vous téléchargez un avatar ou un monde d'avatar qui dépasse nos recommandations, ce monde ou cet avatar peut être supprimé de l'accès public.

# Shaders
VRChat sur Quest ne permet que les shaders fournis avec le dernier SDK sur les avatars. Les shaders sont répertoriés ci-dessous avec une brève description et leurs entrées. Cette liste peut changer, et nous l'annoncerons dans nos notes de mise à jour lorsque de nouveaux shaders seront disponibles.

Tous les shaders répertoriés ci-dessous se trouvent sous `VRChat/Mobile` dans la boîte de dialogue de sélection de shader.

**Pour des raisons de performances, assurez-vous toujours d'activer "Activer l'instanciation GPU" sur vos matériaux.**

Bien sûr ! Voici les informations reformatées sous forme d'un tableau markdown à deux colonnes :

| Nom du Shader           | Description du Shader |
| :-- | :-- |
| Standard Lite           | Une version "Lite" de Unity Standard. Prise en charge des textures diffuses, des cartes de normal, des cartes de métal et de lissage, et des cartes d'émission facultatives. Les mappages des canaux pour les textures pertinentes sont identiques à la configuration métallique standard d'Unity. La texture diffuse est teintée par les couleurs de sommet |
| Bumped Diffuse          | Diffuse mais avec une carte de normal. La texture diffuse est teintée par les couleurs de sommet. |
| Bumped Mapped Specular  | Diffuse, mais avec une carte de spéculaire (brillance) sur le canal alpha. La texture diffuse est teintée par les couleurs de sommet. La carte de normal est également prise en charge. |
| Diffuse                 | Juste diffuse ! La texture diffuse est teintée par les couleurs de sommet. |
| Matcap Lit              | Diffuse, mais avec une entrée Matcap. Peut être utilisé pour simuler une surface métallique brillante. La texture diffuse est teintée par les couleurs de sommet. |
| Toon Lit                | Fournit un ombrage et des ombres de style toon. Doit être utilisé sur des personnages de bande dessinée avec des couleurs unies. La texture diffuse est teintée par les couleurs de sommet. |
| Particles/Additive      | Doit être utilisé sur les particules. Mélange en utilisant le mode Additif. |
| Particles/Multiply      | Doit être utilisé sur les particules. Mélange en utilisant le mode Multiplication. |
| Lightmapped (uniquement pour les mondes) | Un shader diffus de base qui prend en charge le lightmapping. Ce shader est uniquement destiné à être utilisé sur les mondes. Il ne peut pas être utilisé sur les avatars. Il ne prend pas en charge l'éclairage en temps réel. |
| Skybox (uniquement pour les mondes) | Ce shader est un shader de ciel optimisé, destiné à être utilisé dans les mondes. |

Le tableau ci-dessus représente les colonnes "Nom du Shader" et "Description du Shader" des informations que vous avez fournies.

Si vous avez d'autres questions ou besoin d'une aide supplémentaire, n'hésitez pas à demander !

# Composants

Les composants suivants ne sont pas pris en charge sur Quest et ne fonctionneront pas. Cette liste peut changer. Nous le signalerons dans les notes de mise à jour et la documentation mise à jour lorsque cela se produira.

| Nom du Shader           | Description du Shader |
| :-- | :-- |
| Dynamic Bones           | Entièrement désactivé dans VRChat Quest. Utilisez [PhysBones](/avatars/avatar-dynamics/physbones) à la place !! |
| Cloth                   | Entièrement désactivé dans VRChat Quest. |
| Caméras                 | Entièrement désactivé sur les avatars dans VRChat Quest. Autorisé pour une utilisation dans les mondes. Faites attention à ne pas en abuser. |
| Lumières                | Entièrement désactivé sur les avatars dans VRChat Quest. |
| Lecteurs vidéo          | Fonctionne avec certaines limitations. En savoir plus dans [Lecteurs vidéo](/worlds/udon/video-players). |
| Post-traitement         | Les systèmes de post-traitement sont entièrement désactivés dans VRChat Quest. Le GPU n'est pas conçu pour gérer ces effets très bien. |
| Sources audio           | Les sources audio sont entièrement désactivées sur les avatars dans VRChat Quest. Les sources audio consomment une quantité significative de ressources CPU et les voix ont la priorité. |
| Objets physiques        | Les rigidbodies, les colliders et les joints sont entièrement désactivés sur les avatars dans VRChat Quest. \n\n Ils sont autorisés dans les mondes, mais faites attention à ne pas en abuser. |
| Systèmes de particules  | Les particules sont fortement limitées sur les avatars dans VRChat Quest, avec des paramètres reflétant les [Limites du système de particules de l'avatar](https://docs.vrchat.com/docs/avatar-particle-system-limits) sur PC. |
| Contraintes             | Les contraintes sont entièrement désactivées sur les avatars dans VRChat Quest. Il n'y a pas de plans pour les activer pour la Quest, car elles ont des problèmes de performances complexes qui ne sont pas résolus par une limite douce ou dure.\n\nAutorisé pour une utilisation dans les mondes. Faites attention à ne pas en abuser, car elles ont un impact sur les performances plus important que ce qui était précédemment pensé, surtout avec les ressources limitées de la Quest. |
| FinalIK                 | Les composants FinalIK personnalisés sont entièrement désactivés sur les avatars dans VRChat Quest.\n\nLes composants FinalIK sont une source illimitée d'utilisation des ressources. Nous n'avons pas actuellement l'intention de les activer sur Quest. |