```
serialize(stream::IO, value)
```

Écrit une valeur arbitraire dans un flux dans un format opaque, de sorte qu'elle puisse être relue par [`deserialize`](@ref). La valeur relue sera aussi identique que possible à l'originale, mais notez que les valeurs `Ptr` sont sérialisées sous forme de motifs de bits tous à zéro (`NULL`).

Un en-tête d'identification de 8 octets est d'abord écrit dans le flux. Pour éviter d'écrire l'en-tête, construisez un `Serializer` et utilisez-le comme premier argument de `serialize`. Voir aussi [`Serialization.writeheader`](@ref).

Le format de données peut changer dans les versions mineures (1.x) de Julia, mais les fichiers écrits par des versions antérieures à 1.x resteront lisibles. La principale exception à cela est lorsque la définition d'un type dans un package externe change. Si cela se produit, il peut être nécessaire de spécifier une version compatible explicite du package concerné dans votre environnement. Renommer des fonctions, même des fonctions privées, à l'intérieur des packages peut également désynchroniser les fichiers existants. Les fonctions anonymes nécessitent une attention particulière : parce que leurs noms sont générés automatiquement, de mineurs changements de code peuvent les renommer. La sérialisation de fonctions anonymes doit être évitée dans les fichiers destinés à un stockage à long terme.

Dans certains cas, la taille des mots (32 ou 64 bits) des machines de lecture et d'écriture doit correspondre. Dans des cas plus rares, le système d'exploitation ou l'architecture doit également correspondre, par exemple lors de l'utilisation de packages contenant du code dépendant de la plateforme.
