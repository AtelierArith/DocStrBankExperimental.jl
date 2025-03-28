```
rand!([rng=default_rng()], A, [S=eltype(A)])
```

Remplissez le tableau `A` avec des valeurs aléatoires. Si `S` est spécifié (`S` peut être un type ou une collection, cf. [`rand`](@ref) pour plus de détails), les valeurs sont choisies aléatoirement dans `S`. Cela équivaut à `copyto!(A, rand(rng, S, size(A)))` mais sans allouer un nouveau tableau.

# Exemples

```jldoctest
julia> rand!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 0.521213795535383
 0.5868067574533484
 0.8908786980927811
 0.19090669902576285
 0.5256623915420473
```
