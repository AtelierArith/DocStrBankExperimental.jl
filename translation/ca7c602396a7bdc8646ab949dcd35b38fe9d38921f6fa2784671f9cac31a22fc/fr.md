```
isascii(c::Union{AbstractChar,AbstractString}) -> Bool
```

Testez si un caractère appartient à l'ensemble des caractères ASCII, ou si cela est vrai pour tous les éléments d'une chaîne.

# Exemples

```jldoctest
julia> isascii('a')
true

julia> isascii('α')
false

julia> isascii("abc")
true

julia> isascii("αβγ")
false
```

Par exemple, `isascii` peut être utilisé comme fonction prédicat pour [`filter`](@ref) ou [`replace`](@ref) pour supprimer ou remplacer les caractères non-ASCII, respectivement :

```jldoctest
julia> filter(isascii, "abcdeγfgh") # supprimer les caractères non-ASCII
"abcdefgh"

julia> replace("abcdeγfgh", !isascii=>' ') # remplacer les caractères non-ASCII par des espaces
"abcde fgh"
```
