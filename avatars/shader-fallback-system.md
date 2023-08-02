

## Mise à niveau du système de substitution 2021.4.2 de VRChat
Les améliorations apportées à la substitution des shaders fonctionnent en utilisant le champ "Tags" en haut du shader.
```text
Tags{"Queue"="Geometry"}
```
Le champ des tags pourrait ressembler à ceci par défaut.

Vous pouvez maintenant ajouter différents tags, sous le nom `VRCFallback`, pour spécifier quel shader de substitution essayer d'utiliser :
```text
Tags{"Queue"="Geometry" "VRCFallback"="Toon"}
```
Certains tags de substitution peuvent être combinés, vous pouvez par exemple utiliser `ToonCutout :`
```text
Tags{"Queue"="Geometry" "VRCFallback"="ToonCutout"}
```
Les tags pris en charge sont les suivants :

```text
Unlit
VertexLit
Toon
Transparent
Cutout
Fade
Particle
Sprite
Matcap
MobileToon
DoubleSided
Hidden //(cela masquera le modèle de la vue si le shader est bloqué, utile pour des effets de raymarching, par exemple.)
```
Toon et Unlit peuvent également être combinés avec les tags Transparent, Cutout, Fade et DoubleSided pour un contrôle plus précis. Toon prend en charge des variations telles que DoubleSided Cutout.
:::caution

Veuillez noter qu'utiliser les tags Transparent ou Fade avec Toon résultera en une substitution par Transparent Unlit. Vous voudrez peut-être en tenir compte lors du choix des tags de substitution.
:::
Spécifier un autre tag entraînera une substitution par le shader Standard.

Si aucun tag n'est fourni, l'ancien système de substitution sera utilisé, suivant le modèle nom du shader, mots clés, etc.

Nous copions également TOUS les paramètres du shader standard vers le matériau de substitution, notamment les suivants :
```text
_MainTex
_MetallicGlossMap
_SpecGlossMap
_BumpMap
_ParallaxMap
_OcclusionMap
_EmissionMap
_DetailMask
_DetailAlbedoMap
_DetailNormalMap
_Color
_EmissionColor
_SpecColor
_Cutoff
_Glossiness
_GlossMapScale
_SpecularHighlights
_GlossyReflections
_SmoothnessTextureChannel
_Metallic
_SpecularHighlights
_GlossyReflections
_BumpScale
_Parallax
_OcclusionStrength
_DetailNormalMapScale
_UVSec
_Mode
_SrcBlend
_DstBlend
_ZWrite
```
## Ancien système de substitution
Lorsqu'un shader est bloqué par le système de sécurité, il est d'abord vérifié s'il correspond à l'un des shaders pré-compilés internes de cette liste :
```text title="Shaders Internes Pré-compilés"
  "Standard",
  "Standard (réglage spéculaire)",
  "Effects/Rim",
  "Effects/GlowAdditiveSimple",
  "Legacy Shaders/Bumped Diffuse",
  "Legacy Shaders/Bumped Specular",
  "Legacy Shaders/Decal",
  "Legacy Shaders/Diffuse",
  "Legacy Shaders/Diffuse Detail",
  "Legacy Shaders/Diffuse Fast",
  "Legacy Shaders/Lightmapped/Diffuse",
  "Legacy Shaders/Lightmapped/Specular",
  "Legacy Shaders/Lightmapped/VertexLit",
  "Legacy Shaders/Parallax Diffuse",
  "Legacy Shaders/Parallax Specular",
  "Legacy Shaders/Reflective/Bumped Diffuse",
  "Legacy Shaders/Reflective/Bumped Specular",
  "Legacy Shaders/Reflective/Bumped Unlit",
  "Legacy Shaders/Reflective/Bumped VertexLit",
  "Legacy Shaders/Reflective/Diffuse",
  "Legacy Shaders/Reflective/Parallax Diffuse",
  "Legacy Shaders/Reflective/Parallax Specular",
  "Legacy Shaders/Reflective/Specular",
  "Legacy Shaders/Reflective/VertexLit",
  "Legacy Shaders/Self-Illum/Bumped Diffuse",
  "Legacy Shaders/Self-Illum/Bumped Specular",
  "Legacy Shaders/Self-Illum/Diffuse",
  "Legacy Shaders/Self-Illum/Parallax Diffuse",
  "Legacy Shaders/Self-Illum/Parallax Specular",
  "Legacy Shaders/Self-Illum/Specular",
  "Legacy Shaders/Self-Illum/VertexLit",
  "Legacy Shaders/Specular",
  "Legacy Shaders/Transparent/Bumped Diffuse",
  "Legacy Shaders/Transparent/Bumped Specular",
  "Legacy Shaders/Transparent/Cutout/Bumped Diffuse",
  "Legacy Shaders/Transparent/Cutout/Bumped Specular",
  "Legacy Shaders/Transparent/Cutout/Diffuse",
  "Legacy Shaders/Transparent/Cutout/Soft Edge Unlit",
  "Legacy Shaders/Transparent/Cutout/Specular",
  "Legacy Shaders/Transparent/Cutout/VertexLit",
  "Legacy Shaders/Transparent/Diffuse",
  "Legacy Shaders/Transparent/Parallax Diffuse",
  "Legacy Shaders/Transparent/Parallax Specular",
  "Legacy Shaders/Transparent/Specular",
  "Legacy Shaders/Transparent/VertexLit",
  "Legacy Shaders/VertexLit",
  "MatCap/Vertex/Textured Lit",
  "Mobile/Bumped Diffuse",
  "Mobile/Bumped Specular",
  "Mobile/Bumped Specular (1 Directional Light)",
  "Mobile/Diffuse",
  "Mobile/Unlit (Supports Lightmap)",
  "Mobile/Particles/Additive",
  "Mobile/Particles/Alpha Blended",
  "Mobile/Particles/Multiply",
  "Mobile/Particles/VertexLit Blended",
  "Particles/~Additive-Multiply",
  "Particles/Additive",
  "Particles/Additive (Soft)",
  "Particles/Alpha Blended",
  "Particles/Alpha Blended Premultiply",
  "Particles/Anim Alpha Blended",
  "Particles/Multiply",
  "Particles/Multiply (Double)",
  "Particles/VertexLit Blended",
  "Sprites/Default",
  "Sprites/Diffuse",
  "Toon/Lit",
  "Toon/Lit (Double)",
  "Toon/Lit Cutout",
  "Toon/Lit Cutout (Double)",
  "Toon/Lit Outline",
  "UI/Default",
  "Unlit/FailShader",
  "VRChat/UI/Default"
```
Si un shader interne correspond, la substitution est un nouveau shader du même type, mais en utilisant le shader pré-compilé en interne. Tous les paramètres sont copiés. Les nouvelles versions ou variantes ne faisant pas partie de cette liste ne fonctionneront pas, car elles seront remplacées.

Si le shader ne correspond à aucun shader interne, le nom du shader (pas le nom de fichier, mais celui fourni dans la première ligne du code source du shader) est utilisé pour rechercher certaines caractéristiques identifiantes et les remplacer par un shader de substitution de type similaire :
```text title="Recherches de noms de shaders de substitution"
  "Unlit",
  "VertexLit",
  "Toon",
  "Outline",
  "Transparent",
  "Fade",
  "Cutout",
  "Particle",
  "Sprite",
  "MatCap"
```
Ces noms peuvent être présents n'importe où dans la chaîne complète du nom du shader.

De plus, certaines propriétés du shader sont recherchées :
```text title="Propriétés du Shader"
"_Ramp" == "Toon"
"_ALPHABLEND_ON" == "Transparent"
"_ALPHATEST_ON" == "Cutout"
```
Toutes les correspondances respectent la casse.

Des tentatives sont faites pour créer un matériau de substitution qui approxime les noms correspondants. Par exemple, les noms contenant "Sprite" se substituent au shader Unity intégré "Sprites/Default".

Vous pouvez combiner "Toon" et "Cutout", ou "Toon" et "Outline" pour des shaders combinés, cependant "Transparent" et "Fade" n'ont pas actuellement de shader Toon Lit et se substituent donc à "Unlit/Transparent".

Le support de "Outline" est très expérimental et peut être supprimé si les performances sont affectées.

Pour les shaders "Toon", le paramètre "_Ramp" est copié (Texture2D).
Pour les shaders "MatCap", le paramètre "_MatCap" est copié (Texture2D).

Si aucun correspondance n'est trouvée dans le nom du shader, un matériau Standard est utilisé.

Une tentative est faite pour transférer les paramètres nommés "_MainTex" et "_Color" vers le shader de substitution. Si aucun des paramètres ne correspond, un shader Matcap est fourni avec la couleur définie sur la couleur du rang de l'utilisateur.

Tout cela est sujet à de nombreux changements alors que nous ajustons le système de substitution des shaders.