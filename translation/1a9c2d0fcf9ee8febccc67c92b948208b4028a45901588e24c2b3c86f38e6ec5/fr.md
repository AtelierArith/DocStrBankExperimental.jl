```
isequal_normalized(s1::AbstractString, s2::AbstractString; casefold=false, stripmark=false, chartransform=identity)
```

Renvoie si `s1` et `s2` sont des chaînes Unicode équivalentes de manière canonique. Si `casefold=true`, ignore la casse (effectue un pliage de casse Unicode) ; si `stripmark=true`, supprime les marques diacritiques et autres caractères combinants.

Comme avec [`Unicode.normalize`](@ref), vous pouvez également passer une fonction arbitraire via le mot-clé `chartransform` (mappant les points de code `Integer` à des points de code) pour effectuer des normalisations personnalisées, telles que [`Unicode.julia_chartransform`](@ref).

!!! compat "Julia 1.8"
    La fonction `isequal_normalized` a été ajoutée dans Julia 1.8.


# Exemples

Par exemple, la chaîne `"noël"` peut être construite de deux manières équivalentes de manière canonique en Unicode, selon que `"ë"` est formé à partir d'un seul point de code U+00EB ou à partir du caractère ASCII `'e'` suivi du caractère combinant U+0308 diacritique.

```jldoctest
julia> s1 = "noël"
"noël"

julia> s2 = "noël"
"noël"

julia> s1 == s2
false

julia> isequal_normalized(s1, s2)
true

julia> isequal_normalized(s1, "noel", stripmark=true)
true

julia> isequal_normalized(s1, "NOËL", casefold=true)
true
```
