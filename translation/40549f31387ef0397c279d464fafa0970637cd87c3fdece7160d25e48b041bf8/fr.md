```
ascii(s::AbstractString)
```

Convertir une chaîne en type `String` et vérifier qu'elle ne contient que des données ASCII, sinon lever une `ArgumentError` indiquant la position du premier octet non-ASCII.

Voir aussi le prédicat [`isascii`](@ref) pour filtrer ou remplacer les caractères non-ASCII.

# Exemples

```jldoctest
julia> ascii("abcdeγfgh")
ERROR: ArgumentError: invalid ASCII at index 6 in "abcdeγfgh"
Stacktrace:
[...]

julia> ascii("abcdefgh")
"abcdefgh"
```
