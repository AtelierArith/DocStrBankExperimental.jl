```
trunc([T,] x)
trunc(x; digits::Integer= [, base = 10])
trunc(x; sigdigits::Integer= [, base = 10])
```

`trunc(x)` renvoie la valeur entière la plus proche du même type que `x` dont la valeur absolue est inférieure ou égale à la valeur absolue de `x`.

`trunc(T, x)` convertit le résultat en type `T`, en lançant une `InexactError` si la valeur tronquée n'est pas représentable en tant que `T`.

Les mots-clés `digits`, `sigdigits` et `base` fonctionnent comme pour [`round`](@ref).

Pour prendre en charge `trunc` pour un nouveau type, définissez `Base.round(x::NewType, ::RoundingMode{:ToZero})`.

Voir aussi : [`%`](@ref rem), [`floor`](@ref), [`unsigned`](@ref), [`unsafe_trunc`](@ref).

# Exemples

```jldoctest
julia> trunc(2.22)
2.0

julia> trunc(-2.22, digits=1)
-2.2

julia> trunc(Int, -2.22)
-2
```
