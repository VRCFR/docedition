

# VRC JSON

[Les Data Dictionaries](/worlds/udon/data-containers/data-dictionaries) et [les Data Lists](/worlds/udon/data-containers/data-lists) incluent des fonctions pour convertir vers et depuis JSON. Une Data List est équivalente à un tableau JSON, et un objet JSON est équivalent à un Data Dictionary avec des clés de type chaîne de caractères.

Consultez [la documentation JSON](https://www.json.org/json-fr.html) pour plus de détails sur le schéma JSON lui-même. Tout ce qui est présenté dans cette page concerne cette implémentation particulière du schéma JSON.

## Fonctions JSON

| Fonction                       | Entrées                         | Sorties                         | Résultat                                                                                                                                                                                                                                                                         |
| ------------------------------ | ------------------------------- | ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| VRCJson.TryDeserializeFromJson | Chaîne d'entrée                 | Booléen de succès, DataToken    | Crée un DataList ou un DataDictionary à partir de la chaîne JSON d'entrée. Si la conversion est réussie, cela retourne true et le token résultant sera soit un DataDictionary soit un DataList. Si la conversion échoue, cela retourne false et met une erreur expliquant la nature du problème dans le token résultant. |
| VRCJson.TrySerializeToJson     | DataToken d'entrée, JsonExportType | Booléen de succès, DataToken    | Tente de convertir un DataDictionary ou un DataList en une chaîne JSON de sortie. Si la conversion est réussie, cela retourne true et le token résultant sera une chaîne contenant le JSON final. Si la conversion échoue, cela retourne false et met une erreur expliquant la nature du problème dans le token résultant. |

Notez qu'en Udon Graph, le préfixe "VRC" est supprimé de tous les noms de classe, vous devez donc rechercher "Json" pour trouver ces fonctions.

## Types et valeurs pris en charge

JSON est une spécification petite, simple et stricte. Les DataLists et les DataDictionaries sont capables de prendre en charge une gamme beaucoup plus large de configurations, ce qui signifie que vous pouvez rencontrer des limitations lors de la conversion des Data containers en JSON. Assurez-vous de connaître ces limitations et évitez d'utiliser ces configurations dans des situations où vous prévoyez d'utiliser JSON.

**JSON ne prend pas en charge les jetons de données de type `Object Reference`.** Si vous avez des références d'objets dans vos Data containers et que vous essayez de les sérialiser en JSON, la fonction SerializeToJson renverra false avec l'erreur `DataError.TypeUnsupported`.

**JSON ne prend en charge que les dictionnaires avec des clés de type chaîne de caractères.** Si vous avez des clés dans vos DataDictionaries qui ne sont pas de type chaîne de caractères et que vous essayez de les sérialiser en JSON, la fonction SerializeToJson renverra false avec l'erreur `DataError.TypeUnsupported`.

**JSON ne prend pas en charge NaN ou Infinity.** Si vous avez des nombres à virgule ou des doubles qui contiennent NaN ou Infinity, la fonction SerializeToJson renverra false avec l'erreur `DataError.ValueUnsupported`.

**JSON ne supporte que les dictionnaires ou les listes en tant que racine.** Si vous utilisez un DataToken de valeur simple sans enfants, la fonction SerializeToJson renverra false avec l'erreur `DataError.TypeUnsupported`.

**JSON ne prend en charge qu'un seul type de nombre.** Il ne fait pas la distinction entre tous les différents types. Par conséquent, lors de la désérialisation à partir de JSON, tous les nombres sont stockés au format `Double`. Si vous avez des jetons de données contenant d'autres types de nombres tels que `int`, `byte` ou `float`, ils peuvent être sérialisés en JSON, mais si vous désérialisez ce même JSON dans des Data Containers, vous constaterez qu'ils sont maintenant des `Doubles`.

## Désérialisation depuis JSON

`VRCJson.TryDeserializeFromJson` est la fonction à utiliser lorsque vous souhaitez convertir du JSON en Data containers. Il est recommandé de l'utiliser comme condition pour un `if` ou `branch` afin de pouvoir choisir ce qui se passe en cas d'échec et en cas de réussite.

Si TryDeserializeFromJson renvoie true, cela signifie qu'il a réussi à convertir votre chaîne JSON en un DataList ou un DataDictionary. Vous devriez ensuite effectuer une vérification de type sur le résultat pour déterminer ce qui se passe dans chaque cas.

Si cela renvoie false, alors la chaîne que vous avez fournie n'était pas un JSON valide. Le DataToken qui vous est donné sera une DataError, et si vous exécutez DataToken.ToString, il vous donnera à la fois l'erreur et une chaîne expliquant plus en détail ce qui s'est passé exactement.

Pour des raisons de performance, VRCJSON ne parse pas tout immédiatement. Au lieu de cela, il ne parse que le niveau supérieur du JSON d'abord. Si le niveau supérieur est valide, mais que vous avez un JSON non valide plus bas dans une structure imbriquée, il est possible que la désérialisation initiale renvoie true. Plus tard, si vous utilisez TryGetValue pour extraire des valeurs à partir de quelque chose qui était invalide, cela renverra false et vous donnera DataError.UnableToParse.

```csharp title="Désérialisation depuis JSON"
if (VRCJson.DeserializeFromJson(json, out DataToken result))
{
    // La désérialisation a réussi ! Voyons ce que nous avons obtenu.
    if (result.TokenType == TokenType.DataDictionary)
    {
        Debug.Log($"Désérialisé avec succès en tant que dictionnaire avec {result.DataDictionary.Count} éléments.");
    }
    else if (result.TokenType == TokenType.DataList)
    {
        Debug.Log($"Désérialisé avec succès en tant que liste avec {result.DataList.Count} éléments.");
    }
    else 
    {
        // Ceci ne devrait pas être possible. Si DeserializeFromJson renvoie true, cela doit être soit un dictionnaire, soit une liste.
    }
} else {
    // La désérialisation a échoué. Voyons quelle était l'erreur.
    Debug.Log($"Échec de la désérialisation du json {json} - {result.ToString()}");
}
```

## Sérialisation vers JSON

`VRCJson.TrySerializeToJson` est la fonction à utiliser lorsque vous voulez convertir des Data containers en JSON. Il est recommandé de l'utiliser comme condition pour un `if` ou `branch` afin de pouvoir choisir ce qui se passe en cas d'échec et en cas de réussite.

Si TrySerializeToJson renvoie true, cela signifie qu'il a réussi à convertir votre DataList ou DataDictionary en une chaîne JSON, et vous pouvez récupérer en toute sécurité la chaîne à partir du token résultant.

```csharp title="Sérialisation vers JSON"
if (VRCJson.SerializeToJson(dictionary, JsonExportType.Beautify, out DataToken json))
{
    // Sérialisation réussie ! Nous pouvons immédiatement extraire la chaîne du token et faire quelque chose avec.
    Debug.Log($"Sérialisé avec succès en json : {json.String}");
} 
else 
{
    // Échec de la sérialisation pour une raison quelconque, en utilisant ToString sur le résultat devrait nous dire pourquoi.
    Debug.Log(json.ToString());
}
```

### JsonExportType

Lors de la sérialisation en JSON, vous pouvez choisir le JsonExportType que vous souhaitez. Si vous voulez quelque chose de lisible par un humain, Beautify est préférable. Si vous voulez quelque chose de compact pour l'envoi sur le réseau, Minify est préférable.

- Beautify : Développe chaque élément sur une nouvelle ligne et ajoute une tabulation par niveau.
- Minify : Tout est conservé sur une seule ligne et les espaces sont réduits au minimum.