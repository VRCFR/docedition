

# Data Tokens

Data Tokens stockent des données. Chaque token stocke une et une seule variable. Les Data Tokens sont utilisés dans les [Dictionnaires de données](/worlds/udon/data-containers/data-dictionaries) et les [Listes de données](/worlds/udon/data-containers/data-lists).

Les Data Tokens peuvent contenir les types de token suivants :

- Null
- Boolean
- SByte
- Byte
- Short
- UShort
- Int
- UInt
- Long
- ULong
- Float
- Double
- String
- Listes de données (stocke d'autres Data Tokens)
- Dictionnaires de données (stocke d'autres Data Tokens)
- Référence d'objet (peut stocker **tout** via un boxing, mais ne peut pas être sérialisée)
- Erreurs de données (une énumération indiquant ce qui s'est mal passé)

## Propriétés

| Propriété      | Résultat                                                                                                                                                                                                                                                                                                                                                          |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TokenType      | Renvoie le TokenType actuel de la variable contenue dans ce DataToken                                                                                                                                                                                                                                                                                             |
| IsNumber       | Renvoie true si le DataToken contient un type numérique. Sinon, renvoie false.                                                                                                                                                                                                                                                                                   |
| IsNull         | Renvoie true si la valeur contenue dans ce DataToken est nulle sous n'importe quelle forme. Les nombres et les booléens ne sont jamais nuls, TokenType.Null est toujours nul, les chaînes de caractères vérifient la nullité mais pas l'absence de valeur, et les références utilisent Utilities.IsValid en interne pour gérer les joueurs qui ont quitté et les objets qui ont été détruits. |
| Boolean        | Renvoie un booléen si le DataToken contient un booléen. Sinon, génère une exception.                                                                                                                                                                                                                                                                             |
| Number         | Renvoie un double si le DataToken contient n'importe quel type numérique. Sinon, génère une exception.                                                                                                                                                                                                                                                          |
| SByte          | Renvoie un entier 8 bits signé (sbyte) si le DataToken contient un sbyte. Sinon, génère une exception.                                                                                                                                                                                                                                                          |
| Byte           | Renvoie un entier non signé 8 bits (byte) si le DataToken contient un byte. Sinon, génère une exception.                                                                                                                                                                                                                                                        |
| Short          | Renvoie un entier 16 bits signé (short) si le DataToken contient un short, un sbyte ou un byte. Sinon, génère une exception.                                                                                                                                                                                                                                      |
| UShort         | Renvoie un entier non signé 16 bits (ushort) si le DataToken contient un ushort ou un byte. Sinon, génère une exception.                                                                                                                                                                                                                                         |
| Int            | Renvoie un entier 32 bits signé (int) si le DataToken contient un int, un sbyte, un byte, un short ou un ushort. Sinon, génère une exception.                                                                                                                                                                                                                     |
| UInt           | Renvoie un entier non signé 32 bits (uint) si le DataToken contient un uint, un byte ou un ushort. Sinon, génère une exception.                                                                                                                                                                                                                                    |
| Long           | Renvoie un entier 64 bits signé (long) si le DataToken contient un long, un sbyte, un byte, un short, un ushort ou un uint. Sinon, génère une exception.                                                                                                                                                                                                        |
| ULong          | Renvoie un entier non signé 64 bits (ulong) si le DataToken contient un ulong, un byte, un ushort ou un uint. Sinon, génère une exception.                                                                                                                                                                                                                          |
| Float          | Renvoie un flottant 32 bits (float) si le DataToken contient un float, un sbyte, un byte, un short, un ushort, un int, un uint, un long ou un ulong. Sinon, génère une exception.                                                                                                                                                                                |
| Double         | Renvoie un flottant 32 bits (double) si le DataToken contient un double ou n'importe quel autre type numérique. Sinon, génère une exception.                                                                                                                                                                                                                     |
| String         | Renvoie une chaîne de caractères si le DataToken contient une chaîne de caractères. Sinon, génère une exception.                                                                                                                                                                                                                                                  |
| DataDictionary | Renvoie un dictionnaire de données si le DataToken contient un dictionnaire de données. Sinon, génère une exception.                                                                                                                                                                                                                                               |
| DataList       | Renvoie une liste de données si le DataToken contient une liste de données. Sinon, génère une exception.                                                                                                                                                                                                                                                         |
| Référence      | Renvoie une référence d'objet si le DataToken cont