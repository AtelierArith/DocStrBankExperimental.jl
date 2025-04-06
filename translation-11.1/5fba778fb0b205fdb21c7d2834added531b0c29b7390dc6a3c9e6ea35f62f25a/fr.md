```
Bool <: Integer
```

Type booléen, contenant les valeurs `true` et `false`.

`Bool` est une sorte de nombre : `false` est numériquement égal à `0` et `true` est numériquement égal à `1`. De plus, `false` agit comme un "zéro fort" multiplicatif contre [`NaN`](@ref) et [`Inf`](@ref) :

```jldoctest
julia> [true, false] == [1, 0]
true

julia> 42.0 + true
43.0

julia> 0 .* (NaN, Inf, -Inf)
(NaN, NaN, NaN)

julia> false .* (NaN, Inf, -Inf)
(0.0, 0.0, -0.0)
```

Les branches via [`if`](@ref) et d'autres conditionnels n'acceptent que `Bool`. Il n'y a pas de valeurs "véridiques" en Julia.

Les comparaisons retournent généralement `Bool`, et les comparaisons diffusées peuvent retourner [`BitArray`](@ref) au lieu d'un `Array{Bool}`.

```jldoctest
julia> [1 2 3 4 5] .< pi
1×5 BitMatrix:
 1  1  1  0  0

julia> map(>(pi), [1 2 3 4 5])
1×5 Matrix{Bool}:
 0  0  0  1  1
```

Voir aussi [`trues`](@ref), [`falses`](@ref), [`ifelse`](@ref).
