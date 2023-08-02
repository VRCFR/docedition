

Les scripts/composants personnalisés ne sont pas autorisés sur les avatars et seront supprimés lors du téléchargement et de l'exécution.

:::caution

La version Oculus Quest de VRChat présente quelques exceptions à cette liste. Consultez [ici](/platforms/android/quest-content-limitations#components) pour plus d'informations.
:::
## VRChat

- VRCAvatarDescriptor
- PipelineManager
- [VRCStation](/worlds/components/vrc_station)
- [VRCPhysBone](/avatars/avatar-dynamics/physbones#vrcphysbone)
- [VRCPhysBoneCollider](/avatars/avatar-dynamics/physbones#vrcphysbonecollider)
- [VRCContactSender](/avatars/avatar-dynamics/contacts#vrccontactsender)
- [VRCContactReceiver](/avatars/avatar-dynamics/contacts#VRCContactReceiver)
- [VRCSpatialAudioSource](/worlds/components/vrc_spatialaudiosource#spatial-audio-on-avatars)
- [*VRC_IKFollower*](https://docs.vrchat.com/docs/vrc_ikfollower) - Déprécié ! Vous devez utiliser des contraintes à la place.

## Unity

- [Transform](https://docs.unity3d.com/Documentation/Manual/class-Transform.html)
- [Animator](https://docs.unity3d.com/Documentation/Manual/class-Animator.html)
- [SkinnedMeshRenderer](https://docs.unity3d.com/Documentation/Manual/class-SkinnedMeshRenderer.html)
- [MeshFilter](https://docs.unity3d.com/Documentation/Manual/class-MeshFilter.html)
- [MeshRenderer](https://docs.unity3d.com/Documentation/Manual/class-MeshRenderer.html)
- [Animation](https://docs.unity3d.com/Documentation/Manual/class-Animation.html)
- [ParticleSystem](https://docs.unity3d.com/Documentation/Manual/class-ParticleSystem.html)
- [ParticleSystemRenderer](https://docs.unity3d.com/Documentation/Manual/PartSysRendererModule.html)
- [ParticleRenderer](https://docs.unity3d.com/Documentation/Manual/class-ParticleRenderer.html)
- [ParticleAnimator](https://docs.unity3d.com/Documentation/Manual/class-ParticleAnimator.html)
- [EllipsoidParticleEmitter](https://docs.unity3d.com/Documentation/Manual/class-EllipsoidParticleEmitter.html)
- [MeshParticleEmitter](https://docs.unity3d.com/Documentation/Manual/class-MeshParticleEmitter.html)
- [TrailRenderer](https://docs.unity3d.com/Documentation/Manual/class-TrailRenderer.html)
- [LineRenderer](https://docs.unity3d.com/Documentation/Manual/class-LineRenderer.html)
- [Cloth](https://docs.unity3d.com/Documentation/Manual/class-Cloth.html)
- [Light](https://docs.unity3d.com/Documentation/Manual/class-Light.html)
- [Collider](https://docs.unity3d.com/Documentation/Manual/CollidersOverview.html)
- [Rigidbody](https://docs.unity3d.com/Documentation/Manual/class-Rigidbody.html)
- [Joints](https://docs.unity3d.com/Documentation/Manual/Joints.html)
- [Camera](https://docs.unity3d.com/Documentation/Manual/class-Camera.html)\*
- [FlareLayer](https://docs.unity3d.com/Documentation/Manual/class-FlareLayer.html)
- [GUILayer](https://docs.unity3d.com/Documentation/Manual/class-GUILayer.html)
- [AudioSource](https://docs.unity3d.com/Documentation/Manual/class-AudioSource.html)
- [AimConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-AimConstraint.html)
- [LookAtConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-LookAtConstraint.html)
- [ParentConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-ParentConstraint.html)
- [PositionConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-PositionConstraint.html)
- [RotationConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-RotationConstraint.html)
- [ScaleConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-ScaleConstraint.html)

\* Pour le porteur de l'avatar et ses amis, les composants de la caméra sont désactivés au chargement. Utilisez une animation pour activer le composant. Pour les non-amis du porteur de l'avatar, les composants de la caméra sont complètement supprimés au chargement.

## [Root Motion (FinalIK)](http://www.root-motion.com/finalikdox/html/index.html)
:::caution Composants FinalIK Modifiés

VRChat a grandement modifié son implémentation de FinalIK. Par conséquent, ces composants peuvent ne pas fonctionner comme documenté.\n\nNous ne soutenons pas directement ou ne testons pas les implémentations personnalisées de FinalIK sur les avatars. Cependant, elles *devraient* fonctionner correctement, et si nous devons intentionnellement en désactiver un ou plusieurs d'entre eux, nous ferons de notre mieux pour informer les créateurs. \n\nSi vous découvrez un bogue, veuillez [nous en informer](https://feedback.vrchat.com).
:::
- [Aim IK](http://www.root-motion.com/finalikdox/html/page1.html)
- [Biped IK](http://www.root-motion.com/finalikdox/html/page4.html)
- [CCDIK](http://www.root-motion.com/finalikdox/html/page5.html)
- [FABRIK](http://www.root-motion.com/finalikdox/html/page6.html)
- [Full Body Biped IK](http://www.root-motion.com/finalikdox/html/page8.html)\*
- [Grounder](http://www.root-motion.com/finalikdox/html/page9.html)
- [Limb IK](http://www.root-motion.com/finalikdox/html/page12.html)
- [Rotation Limits](http://www.root-motion.com/finalikdox/html/page14.html)
- [VRIK](http://www.root-motion.com/finalikdox/html/page16.html)\*
- Twist Relaxer
- Shoulder Rotator

\* Utiliser ce script sur un avatar humanoïde le cassera.

## [DynamicBone](https://assetstore.unity.com/packages/tools/animation/dynamic-bone-16743)
:::danger Dynamic Bone Déprécié

Le support de Dynamic Bone est déprécié. Vous devez utiliser les [PhysBones](/avatars/avatar-dynamics/physbones) à la place.

:::

- DynamicBone
- DynamicBoneCollider