```
isvalid(s::AbstractString, i::Integer) -> Bool
```

Prédicat indiquant si l'index donné est le début de l'encodage d'un caractère dans `s` ou non. Si `isvalid(s, i)` est vrai, alors `s[i]` renverra le caractère dont l'encodage commence à cet index, si c'est faux, alors `s[i]` lèvera une erreur d'index invalide ou une erreur de limites selon que `i` est dans les limites. Pour que `isvalid(s, i)` soit une fonction O(1), l'encodage de `s` doit être [auto-synchronisant](https://en.wikipedia.org/wiki/Self-synchronizing_code). C'est une hypothèse de base du support des chaînes génériques de Julia.

Voir aussi [`getindex`](@ref), [`iterate`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref), [`length`](@ref).

# Exemples

```jldoctest
julia> str = "αβγdef";

julia> isvalid(str, 1)
true

julia> str[1]
'α': Unicode U+03B1 (catégorie Ll: Lettre, minuscule)

julia> isvalid(str, 2)
false

julia> str[2]
ERROR: StringIndexError: index invalide [2], indices valides à proximité [1]=>'α', [3]=>'β'
Stacktrace:
[...]
```
