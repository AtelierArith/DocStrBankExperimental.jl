```
 isidentifier(s) -> Bool
```

Retourne si le symbole ou la chaîne `s` contient des caractères qui sont analysés comme un identifiant ordinaire valide (pas un opérateur binaire/uniaire) dans le code Julia ; voir aussi [`Base.isoperator`](@ref).

En interne, Julia permet toute séquence de caractères dans un `Symbol` (sauf les `\0`), et les macros utilisent automatiquement des noms de variables contenant `#` afin d'éviter les collisions de noms avec le code environnant. Pour que le parseur reconnaisse une variable, il utilise un ensemble limité de caractères (grandement étendu par Unicode). `isidentifier()` permet de vérifier directement auprès du parseur si un symbole contient des caractères valides.

# Exemples

```jldoctest
julia> Meta.isidentifier(:x), Meta.isidentifier("1x")
(true, false)
```
