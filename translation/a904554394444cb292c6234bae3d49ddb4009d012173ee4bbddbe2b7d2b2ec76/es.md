```
rand!([rng=default_rng()], A, [S=eltype(A)])
```

Puebla el arreglo `A` con valores aleatorios. Si `S` se especifica (`S` puede ser un tipo o una colección, cf. [`rand`](@ref) para más detalles), los valores se eligen aleatoriamente de `S`. Esto es equivalente a `copyto!(A, rand(rng, S, size(A)))` pero sin asignar un nuevo arreglo.

# Ejemplos

```jldoctest
julia> rand!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 0.521213795535383
 0.5868067574533484
 0.8908786980927811
 0.19090669902576285
 0.5256623915420473
```
