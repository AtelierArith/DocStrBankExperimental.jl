```
unsafe_trunc(T, x)
```

Renvoie la valeur entière la plus proche de type `T` dont la valeur absolue est inférieure ou égale à la valeur absolue de `x`. Si la valeur n'est pas représentable par `T`, une valeur arbitraire sera renvoyée. Voir aussi [`trunc`](@ref).

# Exemples

```jldoctest
julia> unsafe_trunc(Int, -2.2)
-2

julia> unsafe_trunc(Int, NaN)
-9223372036854775808
```
