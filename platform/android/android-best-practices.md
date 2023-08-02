

Rendre vos mondes VRChat compatibles avec plusieurs plateformes est un excellent moyen de permettre à un plus grand nombre de joueurs d'en profiter. La plupart des joueurs de VRChat utilisent Android, il est donc intéressant de créer une version Android de votre monde VRChat.

Cependant, les joueurs sur smartphone et les joueurs en réalité virtuelle vivront votre monde de manière assez différente ! Dans ce guide, nous vous expliquerons quelques astuces pour rendre votre monde VRChat sur appareils mobiles plus confortable et plus agréable.
:::info

VRChat n'est pas encore disponible sur Android.
Sa sortie est prévue plus tard cette année.

:::
## 1. Publiez votre monde VRChat sur Android

Il est toujours judicieux de publier votre monde sur PC et sur toutes les autres plateformes prises en charge par VRChat.

Tous les mondes téléchargés sur Android sont disponibles sur l'Oculus Quest 2 et sur les téléphones Android. Si vous avez déjà publié une version pour Quest de votre monde, elle sera également disponible sur les téléphones !

Pour apprendre comment télécharger votre monde sur Android, veuillez consulter notre [documentation sur la configuration multiplateforme](https://creators.vrchat.com/platforms/android/cross-platform-setup).

:::note

Si vous voyez le terme « Quest » en référence au kit de développement logiciel (SDK) VRChat, cela s'applique généralement également à Android.

Par exemple : les outils existants comme [EasyQuestSwitch](https://vcc.docs.vrchat.com/vpm/curated-community-packages#easyquestswitch) sont excellents pour le développement multiplateforme. Un Meta Quest n'est pas nécessaire !

:::

## 2. Détectez automatiquement les joueurs sur appareils mobiles dans votre monde

Lorsqu'un joueur Android rejoint votre monde, vous souhaiterez peut-être modifier certains aspects de celui-ci. Les joueurs sur téléphone Android n'ont pas accès aux contrôleurs de réalité virtuelle, tout comme les joueurs en réalité virtuelle n'ont pas accès à un écran tactile.

Vous pouvez utiliser [UdonSharp](https://udonsharp.docs.vrchat.com/) pour détecter les joueurs Android dans votre monde :

```
public bool _UtiliseUnTelephone()
{
  #if UNITY_ANDROID
  return !VRC.SDKBase.Networking.LocalPlayer.IsUserInVR();
  #endif
  return false;
}
```

Voici comment cela fonctionne :

- Utilisez [la compilation conditionnelle](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) pour détecter la plateforme actuelle.
- Utilisez [Networking.LocalPlayer](https://creators.vrchat.com/worlds/udon/players/) pour récupérer des données sur le joueur local.
- Utilisez [IsUserInVR](https://creators.vrchat.com/worlds/udon/players/#isuserinvr) pour vérifier si le joueur local est en réalité virtuelle.

Si le joueur local est sur Android, mais n'est pas en réalité virtuelle, cela signifie qu'il joue sur un téléphone Android.

Nous travaillons sur un moyen de détecter facilement les plateformes de cette manière, que ce soit avec Udon Graph ou UdonSharp.

## 3. Optimisez votre monde pour Android

Les appareils Android sont généralement moins puissants que les PC. Lisez notre guide d'optimisation du contenu pour Quest (en anglais) pour améliorer les performances de votre monde.

Bonne nouvelle : si votre monde fonctionne correctement sur le Quest 2, il fonctionnera probablement bien sur les téléphones Android. Les téléphones ont une résolution inférieure aux casques de réalité virtuelle, et les problèmes de performance causeront moins de nausées que dans la réalité virtuelle.

Veillez tout de même à ce que les joueurs sur Quest 2 aient un taux de rafraîchissement acceptable.

## 4. Testez votre monde sur Android

Tester votre monde sur un téléphone Android vous aidera à améliorer l'expérience des joueurs sur appareils mobiles. Même si votre monde est encore au stade de développement précoce, pensez à la manière dont il se jouera sur un appareil mobile.

Lorsque vous itérez rapidement sur vos mondes VRChat, il peut être pratique de les tester dans l'éditeur Unity ou dans la version Steam de VRChat. Une manette de jeu peut être un substitut approprié à l'écran de contrôle mobile de VRChat.

- Sur un écran tactile, des joysticks _virtuels_ contrôlent les mouvements et la caméra du joueur.
- Les écrans tactiles permettent des interactions plus faciles avec d'autres dispositifs d'entrée.
- Testez votre monde avec des joueurs sur appareils mobiles.

## 5. Concevez vos interfaces utilisateur pour les écrans tactiles

Les écrans de téléphone sont différents des PC et des appareils de réalité virtuelle. Vous voudrez peut-être ajuster vos interfaces utilisateur pour les rendre plus faciles à lire et à utiliser pour les utilisateurs mobiles.

- Le texte de votre interface utilisateur doit être facile à lire. Utilisez des polices lisibles, des tailles de texte importantes et de gros boutons.
- Évitez de vous appuyer sur des interactions qui nécessitent un dispositif de réalité virtuelle ou des mouvements de caméra complexes.
- Essayez d'utiliser les [interfaces utilisateur en espace-écran](https://docs.unity3d.com/Packages/com.unity.ugui@2.0/manual/UICanvas.html). Sur un écran tactile, elles sont plus faciles à utiliser que les toiles d'espace-monde. Envisagez d'ajouter une interface utilisateur que les utilisateurs peuvent ouvrir de n'importe où sans avoir besoin de se rendre à un panneau de menu dans le monde.

---

En suivant ces étapes, vous rendrez votre monde VRChat pour les joueurs sur appareils mobiles une expérience exceptionnelle.

Avez-vous des conseils ou des astuces que vous souhaitez que nous incluions dans cet article ? Soumettez vos commentaires ci-dessous et nous ferons de notre mieux pour aider à partager vos connaissances avec la communauté VRChat.