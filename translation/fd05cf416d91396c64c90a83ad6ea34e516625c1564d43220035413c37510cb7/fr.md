```
list(tarball; [ strict = true ]) -> Vector{Header}
list(callback, tarball; [ strict = true ])

    callback  :: Header, [ <data> ] --> Any
    tarball   :: Union{AbstractString, AbstractCmd, IO}
    strict    :: Bool
```

Liste le contenu d'une archive tar ("tarball") située à l'emplacement `tarball`. Si `tarball` est un handle IO, lis le contenu tar à partir de ce flux. Renvoie un vecteur de structures `Header`. Voir [`Header`](@ref) pour plus de détails.

Si un `callback` est fourni, alors au lieu de renvoyer un vecteur d'en-têtes, le callback est appelé sur chaque `Header`. Cela peut être utile si le nombre d'éléments dans le tarball est important ou si vous souhaitez examiner les éléments avant une erreur dans le tarball. Si la fonction `callback` peut accepter un deuxième argument de type `Vector{UInt8}` ou `Vector{Pair{Symbol, String}}`, alors elle sera appelée avec une représentation des données d'en-tête brutes soit sous forme de vecteur d'octets unique, soit sous forme de vecteur de paires associant les noms de champs aux données brutes pour ce champ (si ces champs sont concaténés, le résultat est les données brutes de l'en-tête).

Par défaut, `list` renverra une erreur si elle rencontre des contenus de tarball que la fonction `extract` refuserait d'extraire. Avec `strict=false`, elle ignorera ces vérifications et listera tous les contenus du fichier tar, que `extract` les extraie ou non. Attention, les tarballs malveillants peuvent faire toutes sortes de choses astucieuses et inattendues pour essayer de vous tromper en faisant quelque chose de mauvais.

Si l'argument `tarball` est un fichier squelette (voir `extract` et `create`), alors `list` détectera cela à partir de l'en-tête du fichier et listera ou itérera de manière appropriée les en-têtes du fichier squelette.
