

VRChat vous permet de créer et de télécharger des avatars personnalisés !

# Création des avatars

Pour commencer, consultez [La création de votre premier avatar](/avatars/creating-your-first-avatar).

Il y a toute une catégorie dédiée aux "Avatars" dans la barre latérale. Voici quelques pages plus importantes et impactantes :

- [Exigences pour le système de rig](/avatars/rig-requirements) explique comment configurer la hiérarchie de votre modèle 3D personnalisé pour VRChat.
- [Système de classement des performances des avatars](/avatars/avatar-performance-ranking-system) explique comment certains avatars obtiennent une performance "Excellente" et d'autres "Très mauvaise".
- [Conseils d'optimisation des avatars](/avatars/avatar-optimizing-tips) - Maintenant que vous savez pourquoi, consultez cette page pour savoir comment retrouver tous vos frames.
- Continuez à lire cette page pour en savoir plus sur les concepts importants du SDK Avatars 3.0.

## Qu'est-ce que Avatars 3.0 ?

**Avatars 3.0** est notre nom pour toutes les fonctionnalités disponibles pour les avatars dans VRChat. Les fonctionnalités d'AV3 sont axées sur l'amélioration de l'expression, des performances et des capacités des avatars dans VRChat.

Avatars 3.0 est étroitement intégré à [Action Menu](https://docs.vrchat.com/docs/action-menu) pour contrôler et interagir avec l'avatar que vous portez. Il est probablement préférable que vous y participiez et essayiez le Action Menu avant de construire un avatar AV3 !

## Prérequis

- [Installer et configurer le SDK Avatars VRChat](/sdk)
- [Créer votre premier avatar](/avatars/creating-your-first-avatar)

## Comprendre les concepts

Pour comprendre et utiliser Avatars 3.0, vous devez connaître quelques concepts. Ces concepts vous aideront à comprendre la construction des avatars, comment les assembler au mieux et l'utilisation prévue de différents systèmes.

### Systèmes Unity

Ce document est rédigé en supposant que vous connaissez un peu [Unity Animators](https://docs.unity3d.com/2019.4/Documentation/Manual/class-AnimatorController.html). En particulier, vous devez avoir une connaissance de base du fonctionnement des éléments suivants :

- Animateurs et animations
- Couches d'animateur, pondérations de couches et fusion
- États et transitions
- Paramètres d'animateur
- Comportements d'état
- Masques d'avatar

Il peut également être utile de connaître des éléments tels que :

- Temps de sortie d'état
- Boucle d'exécution pour les animations
- (Avancé) Synchronisation du temps entre les couches
- (Avancé) Arbres de fusion

### Bases

Avec Avatars 3.0, vous pouvez créer rapidement un avatar de base avec un mouvement oculaire simulé et des visèmes. 

1. Importez votre avatar, riguez-le en tant qu'humanoïde\*\*. Configurer vos matériaux, etc.
2. Ajoutez le composant Avatar Descriptor.
3. Définissez les os des yeux si vous souhaitez avoir un mouvement oculaire simulé.
4. Définissez le type de visème si vous souhaitez des visèmes. Attribuez l'os de la mâchoire dans l'écran de configuration du rigging, ou définissez vos visèmes par des blendshapes. Comme pour l'Avatar 2.0.
5. Définissez votre point de vue.
6. Construisez et téléchargez !

\*\* Si vous créez un avatar non humanoïde, veuillez lire la section des avatars génériques ci-dessous.

C'est terminé ! Cela créera un avatar de base avec des gestes et des actions par défaut. Il y a quelques fonctionnalités intégrées que vous pouvez exploiter, donc même si quelqu'un met un avatar avec des blendshapes/os de certains noms, vous obtiendrez certaines fonctionnalités basiques de l'Avatar 3.0.

Cependant, même avec ces systèmes de base améliorés, il y a certaines nouvelles fonctionnalités.

### Test d'avatar local

Vous avez déjà voulu itérer et tester un avatar sans le télécharger ? Eh bien, avec Avatars 3.0, maintenant vous pouvez !

Dans l'onglet "Builder" du panneau de contrôle du SDK VRChat, vous pouvez maintenant sélectionner "Build & Test" dans la section "Offline Testing". Lorsque vous cliquez sur cela, votre avatar sera construit, puis copié dans un dossier.

Lorsque vous lancez VRChat, vous pourrez accéder à cet avatar localement en regardant la section "Autres" du menu Avatar ! Vous seul pourrez le voir, mais vous pouvez apporter des modifications à votre avatar, cliquer sur "Build & Test" à nouveau, et après une courte construction, votre avatar sera mis à jour. Il vous suffit de sélectionner à nouveau l'avatar dans votre menu et de cliquer de nouveau sur "Changer", et vous basculerez vers le nouvel avatar de test.

Cet avatar est _uniquement_ visible pour vous ! Pour tout le monde, vous aurez l'air de porter le dernier avatar que vous portiez avant de passer à l'avatar de test local. Pour nos testeurs AV3, cela a permis d'accélérer énormément l'itération. Nous espérons que cela vous plaira !

Pour supprimer l'avatar de test local copié, allez à l'onglet "Content Manager" du panneau de contrôle du SDK VRChat. Vous verrez votre avatar dans la section "Test Avatars" en bas. Cliquez sur "Supprimer" et