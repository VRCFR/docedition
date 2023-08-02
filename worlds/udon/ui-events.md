

Vous pouvez utiliser les événements d'interface utilisateur Unity pour appeler directement des méthodes pour des interactions simples, plutôt que de créer un UdonBehaviour. 

![ui-events-3c37d22-UIEventTarget.png](/img/worlds/ui-events-3c37d22-UIEventTarget.png)

Cependant, nous avons limité ce qui peut être appelé à cette liste :

# Cibles autorisées pour les événements d'interface utilisateur

### Animator
* Play
* PlayInFixedTime
* Rebind
* SetBool
* SetFloat
* SetInteger
* SetTrigger
* ResetTrigger
* speed

### AudioSource
* Pause
* Play
* PlayDelayed
* PlayOneShot
* Stop
* UnPause
* bypassEffects
* bypassListenerEffects
* bypassReverbZones
* dopplerLevel
* enabled
* loop
* maxDistance
* rolloffMode
* minDistance
* mute
* pitch
* playOnAwake
* priority
* spatialize
* spread
* time
* volume

### AudioDistortionFilter
* decayRatio
* delay
* dryMix
* enabled
* wetMix

### AudioEchoFilter
* decayRatio
* delay
* dryMix
* enabled
* wetMix

### AudioHighPassFilter
* cutoffFrequency
* enabled
* highpassResonanceQ

### AudioLowPassFilter
* cutoffFrequency
* enabled
* lowpassResonanceQ

### AudioReverbFilter
* decayHFRatio
* decayTime
* density
* diffusion
* dryLevel
* enabled
* hfReference
* reflectionsDelay
* reflectionsLevel
* reverbDelay
* reverbLevel
* room
* roomHF
* roomLF

### AudioReverbZone
* decayHFRatio
* decayTime
* density
* diffusion
* enabled
* HFReference
* LFReference
* maxDistance
* minDistance
* reflections
* reflectionsDelay
* room
* roomHF
* roomLF

### Button
* enabled
* interactable
* targetGraphic

### Collider
* enabled
* isTrigger

### Dropdown
* captionText
* enabled
* interactable
* itemText
* targetGraphic
* template
* value

### Image
* alphaHitTestMinimumThreshold
* enabled
* fillAmount
* fillCenter
* fillClockwise
* fillOrigin
* maskable
* preserveAspect
* raycastTarget
* useSpriteMesh

### GameObject
* SetActive

### InputField
:::caution Limite de caractères
Veuillez noter que les champs de saisie sont limités à 16 000 caractères, qui est le nombre maximal de caractères qu'un composant texte peut afficher.
:::
* ForceLabelUpdate
* caretBlinkRate
* caretPosition
* caretWidth
* characterLimit
* customCaretColor
* enabled
* interactable
* readOnly
* selectionAnchorPosition
* text
* textComponent
* selectionFocusPosition

### Light
* Reset
* bounceIntensity
* colorTemperature
* cookie
* enabled
* intensity
* range
* shadowBias
* shadowNearPlane
* shadowNormalBias
* shadowStrength
* spotAngle

### LineRenderer
* allowOcclusionWhenDynamic
* shadowCastingMode
* enabled
* endWidth
* loop
* motionVectorGenerationMode
* numCapVertices
* numCornerVertices
* probeAnchor
* receiveShadows
* shadowBias
* startWidth
* lightProbeUsage
* useWorldSpace
* widthMultiplier

### Mask
* enabled
* showMaskGraphic

### MeshRenderer
* shadowCastingMode
* enabled
* probeAnchor
* receiveShadows
* lightProbeUsage

### ParticleSystem
* Clear
* Emit
* Pause
* Pause
* Play
* Simulate
* Stop
* Stop
* TriggerSubEmitter
* time
* useAutoRandomSeed

### ParticleSystemForceField
* endRange
* gravityFocus
* length
* multiplyDragByParticleSize
* multiplyDragByParticleVelocity
* startRange

### Projector
* aspectRatio
* enabled
* nearClipPlane
* farClipPlane
* fieldOfView
* orthographic
* orthographicSize

### RawImage
* enabled
* maskable
* raycastTarget

### RectMask2D
* enabled

### Scrollbar
* enabled
* handleRect
* interactable
* numberOfSteps
* size
* targetGraphic
* value

### ScrollRect
* content
* decelerationRate
* elasticity
* enabled
* horizontal
* horizontalNormalizedPosition
* horizontalScrollbar
* horizontalScrollbarSpacing
* inertia
* scrollSensitivity
* vertical
* verticalNormalizedPosition
* verticalScrollbar
* verticalScrollbarSpacing
* viewport

### Selectable
* enabled
* interactable
* targetGraphic

### SkinnedMeshRenderer
* allowOcclusionWhenDynamic
* shadowCastingMode
* enabled
* lightProbeProxyVolumeOverride
* motionVectorGenerationMode
* probeAnchor
* receiveShadows
* rootBone
* skinnedMotionVectors
* updateWhenOffscreen
* lightProbeUsage

### Slider
* enabled
* fillRect
* handleRect
* interactable
* maxValue
* minValue
* normalizedValue
* targetGraphic
* value
* wholeNumbers

### Text
* alignByGeometry
* enabled
* fontSize
* lineSpacing
* maskable
* raycastTarget
* resizeTextForBestFit
* resizeTextMaxSize
* resizeTextMinSize
* supportRichText
* text

### Toggle
* enabled
* group
* interactable
* isOn
* targetGraphic

### ToggleGroup
* allowSwitchOff
* enabled

### TrailRenderer
* Clear
* allowOcclusionWhenDynamic
* autodestruct
* shadowCastingMode
* enabled
* emitting
* endWidth
* motionVectorGenerationMode
* numCapVertices
* numCornerVertices
* probeAnchor
* receiveShadows
* shadowBias
* startWidth
* lightProbeUsage
* widthMultiplier

### UdonBehaviour
* RunProgram
* SendCustomEvent
* Interact