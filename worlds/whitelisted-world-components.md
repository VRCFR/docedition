

Le texte suivant est la liste complète des scripts utilisables dans les mondes. Les composants qui ne figurent pas dans cette liste ne fonctionneront pas.

:::caution[Oculus Quest]
La version Oculus Quest de VRChat présente quelques exceptions à cette liste. Consultez [ici](/platforms/android/quest-content-limitations#components) pour plus d'informations.
:::
## Composants Unity
- WindZone
- VideoPlayer
- Tilemap
- TilemapRenderer
- Terrain
- Tree
- SpriteMask
- ParticleEmitter
- EllipsoidParticleEmitter
- MeshParticleEmitter
- ParticleAnimator
- ParticleRenderer
- WorldParticleCollider
- Grid
- GridLayout
- AudioSource
- AudioReverbZone
- AudioLowPassFilter
- AudioHighPassFilter
- AudioDistortionFilter
- AudioEchoFilter
- AudioChorusFilter
- AudioReverbFilter
- PlayableDirector
- TerrainCollider
- Canvas
- CanvasGroup
- CanvasRenderer
- TextMesh
- Animator
- NavMeshAgent
- NavMeshObstacle
- OffMeshLink
- Cloth
- WheelCollider
- Rigidbody
- Joint
- HingeJoint
- SpringJoint
- FixedJoint
- CharacterJoint
- ConfigurableJoint
- ConstantForce
- Collider
- BoxCollider
- SphereCollider
- MeshCollider
- CapsuleCollider
- ParticleSystem
- ParticleSystemRenderer
- BillboardRenderer
- Camera
- FlareLayer
- SkinnedMeshRenderer
- TrailRenderer
- LineRenderer
- GUIElement
- GUILayer
- Light
- LightProbeGroup
- LightProbeProxyVolume
- LODGroup
- ReflectionProbe
- SpriteRenderer
- Transform
- RectTransform
- Rendering.SortingGroup
- Projector
- OcclusionPortal
- OcclusionArea
- LensFlare
- Skybox
- MeshFilter
- Halo
- MeshRenderer

### Composants Unity
- [ParticleSystemForceField](https://docs.unity3d.com/2019.4/Documentation/Manual/class-ParticleSystemForceField.html)
- [AimConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-AimConstraint.html)
- [LookAtConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-LookAtConstraint.html)
- [ParentConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-ParentConstraint.html)
- [PositionConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-PositionConstraint.html)
- [RotationConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-RotationConstraint.html)
- [ScaleConstraint](https://docs.unity3d.com/2019.4/Documentation/Manual/class-ScaleConstraint.html)

## Composants VRChat
- [*VRC_IKFollower*](https://docs.vrchat.com/docs/vrc_ikfollower) - Obsolète. Utilisez [Constraints](https://docs.unity3d.com/2019.4/Documentation/Manual/Constraints.html) à la place !
- [VRC_AvatarPedestal](/worlds/components/vrc_avatarpedestal)
- [VRC_PortalMarker](/worlds/components/vrc_portalmarker)
- [VRC_MirrorReflection](/worlds/components/vrc_mirrorreflection)
- [VRC_SceneDescriptor](/worlds/components/vrc_scenedescriptor)
- [VRC_SpatialAudioSource](/worlds/components/vrc_spatialaudiosource)
- [VRC_Station](/worlds/components/vrc_station)
- [VRC_UiShape](/worlds/components/vrc_uishape)
- [VRCPipelineManager](/sdk/vrcpipelinemanager)

## Dynamic Bone
- DynamicBone
- DynamicBoneCollider

## Text Mesh Pro
- InlineGraphic
- InlineGraphicManager
- TMP_Dropdown
- TMP_InputField
- TMP_ScrollbarEventHandler
- TMP_SelectionCaret
- TMP_SpriteAnimator
- TMP_SubMesh
- TMP_SubMeshUI
- TMP_Text
- TextMeshPro
- TextMeshProUGUI
- TextContainer
- TMP_Dropdown

## Système d'événements Unity
- EventSystem
- EventTrigger
- UIBehaviour
- BaseInput
- BaseInputModule
- PointerInputModule
- StandaloneInputModule
- TouchInputModule
- BaseRaycaster
- PhysicsRaycaster

## Interface utilisateur Unity
- Button
- Dropdown
- Dropdown
- Graphic
- GraphicRaycaster
- Image
- InputField
- Mask
- MaskableGraphic
- RawImage
- RectMask2D
- Scrollbar
- ScrollRect
- Selectable
- Slider
- Text
- Toggle
- ToggleGroup
- AspectRatioFitter
- CanvasScaler
- ContentSizeFitter
- GridLayoutGroup
- HorizontalLayoutGroup
- HorizontalOrVerticalLayoutGroup
- LayoutElement
- LayoutGroup
- VerticalLayoutGroup
- BaseMeshEffect
- Outline
- PositionAsUV1
- Shadow

## Post Processing Stack V2
:::caution Post Processing Stack v1

PPSv1 n'est pas pris en charge dans VRCSDK2 ni dans VRCSDK3. Il a été abandonné par Unity.
:::
- PostProcessDebug
- PostProcessLayer
- PostProcessVolume

## AVPro
- ApplyToMaterial
- ApplyToMesh
- AudioOutput
- CubemapCube
- DebugOverlay
- DisplayBackground
- DisplayIMGUI
- DisplayUGUI
- MediaPlayer
- StreamParser
- SubtitlesUGUI
- UpdateStereoMaterial

## Oculus Spatializer Unity
- ONSPReflectionZone
- OculusSpatializerUnity
- ONSPAmbisonicsNative
- ONSPAudioSource

## Final IK
- BipedIK
- FingerRig
- Grounder
- GrounderBipedIK
- GrounderFBBIK
- GrounderIK
- GrounderQuadruped
- GrounderVRIK
- AimIK
- CCDIK
- FABRIK
- FABRIKRoot
- FullBodyBipedIK
- IK
- IKExecutionOrder
- LegIK
- LimbIK
- LookAtIK
- TrigonometricIK
- VRIK
- FBBIKArmBending
- FBBIKHeadEffector
- TwistRelaxer
- InteractionObject
- InteractionSystem
- InteractionTarget
- InteractionTrigger
- GenericPoser
- HandPoser
- Poser
- RagdollUtility
- RotationLimit
- RotationLimitAngle
- RotationLimitHinge
- RotationLimitPolygonal
- RotationLimitSpline
- AimPoser
- Amplifier
- BodyTilt
- HitReaction
- HitReactionVRIK
- Inertia
- OffsetModifier
- OffsetModifierVRIK
- OffsetPose
- Recoil
- ShoulderRotator
- AnimationBlocker
- BehaviourAnimatedStagger
- BehaviourBase
- BehaviourFall
- BehaviourPuppet
- JointBreakBroadcaster
- MuscleCollisionBroadcaster
- PressureSensor
- Prop
- PropRoot
- PuppetMaster
- PuppetMasterSettings
- BipedRagdollCreator
- RagdollCreator
- RagdollEditor
- SolverManager
- TriggerEventBroadcaster