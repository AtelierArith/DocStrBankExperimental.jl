```
convert(T, x)
```

Convertir `x` en une valeur de type `T`.

Si `T` est un type [`Integer`](@ref), une [`InexactError`](@ref) sera levée si `x` n'est pas représentable par `T`, par exemple si `x` n'est pas de valeur entière, ou est en dehors de la plage supportée par `T`.

# Exemples

```jldoctest
julia> convert(Int, 3.0)
3

julia> convert(Int, 3.5)
ERROR: InexactError: Int64(3.5)
Stacktrace:
[...]
```

Si `T` est un type [`AbstractFloat`](@ref), alors il renverra la valeur la plus proche de `x` représentable par `T`. Inf est traité comme un ulp de plus que `floatmax(T)` pour déterminer le plus proche.

```jldoctest
julia> x = 1/3
0.3333333333333333

julia> convert(Float32, x)
0.33333334f0

julia> convert(BigFloat, x)
0.333333333333333314829616256247390992939472198486328125
```

Si `T` est un type de collection et `x` une collection, le résultat de `convert(T, x)` peut faire référence à tout ou partie de `x`.

```jldoctest
julia> x = Int[1, 2, 3];

julia> y = convert(Vector{Int}, x);

julia> y === x
true
```

Voir aussi : [`round`](@ref), [`trunc`](@ref), [`oftype`](@ref), [`reinterpret`](@ref).
