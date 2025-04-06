```
peek(stream[, T=UInt8])
```

Lire et retourner une valeur de type `T` à partir d'un flux sans avancer la position actuelle dans le flux. Voir aussi [`startswith(stream, char_or_string)`](@ref).

# Exemples

```jldoctest
julia> b = IOBuffer("julia");

julia> peek(b)
0x6a

julia> position(b)
0

julia> peek(b, Char)
'j': ASCII/Unicode U+006A (catégorie Ll: Lettre, minuscule)
```

!!! compat "Julia 1.5"
    La méthode qui accepte un type nécessite Julia 1.5 ou version ultérieure.

