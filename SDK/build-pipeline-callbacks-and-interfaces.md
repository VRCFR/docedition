

Le SDK VRChat contient plusieurs interfaces qui peuvent être utilisées via des scripts d'éditeur pour améliorer le processus de construction des Mondes et des Avatars.

## Pour les Composants de Scène

Les interfaces décrites ci-dessous peuvent être utilisées en combinaison avec des `MonoBehaviours` et, par conséquent, être placées directement sur des objets de la scène, ce qui peut être utile dans une situation où vous avez besoin de conserver certaines références spécifiques de la scène pour effectuer vos modifications.

### IEditorOnly

`VRC.SDKBase.IEditorOnly`

L'interface n'a aucun membre à implémenter.

Vous pouvez utiliser `IEditorOnly` pour marquer un script comme réservé à l'éditeur pour la Validation du SDK. Cela signifie que le SDK l'ignorera lors de l'analyse de votre Monde ou de votre Avatar à la recherche de scripts incompatibles.

### IPreprocessCallbackBehaviour

`VRC.SDKBase.IPreprocessCallbackBehaviour`

Membres à implémenter

```csharp
public void OnPreprocess()
{
}

public int PreprocessOrder { get; }
```

Cette interface vous permet d'exécuter du code personnalisé lorsque le processus de construction est sur le point de commencer. Cela peut être utile si vous devez effectuer des modifications avant que le contenu ne soit construit et téléchargé sur VRChat.

> 🚧 Notez que cela ne contourne pas automatiquement la validation du SDK. Vous devez également utiliser `IEditorOnly` si vos scripts se trouvent directement sur l'avatar que vous téléchargez

## Pour les Scripts au Niveau du Projet

Ces interfaces conviennent à tout ce qui ne dépend pas d'objets de scène particuliers et effectue des modifications en vrac sur la scène/l'avatar avant qu'il ne soit téléchargé sur VRChat.

### IVRCSDKBuildRequestedCallback

`VRC.SDKBase.Editor.BuildPipeline.IVRCSDKBuildRequestedCallback`

Membres à implémenter

```csharp
    public int callbackOrder => 0;

    public bool OnBuildRequested(VRCSDKRequestedBuildType requestedBuildType)
    {
        return true;
    }
```

Où `VRCSDKRequestedBuildType` est une énumération de la forme suivante

```csharp
public enum VRCSDKRequestedBuildType
{
    Avatar,
    Scene,
}
```

Cette interface vous permet d'exécuter une logique avant que le SDK VRChat ne commence à construire le contenu.

`OnBuildRequested` peut également interrompre la construction en renvoyant `false`.