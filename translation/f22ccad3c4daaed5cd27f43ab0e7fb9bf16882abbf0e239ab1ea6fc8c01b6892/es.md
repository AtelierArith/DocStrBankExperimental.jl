```
eigvecs(A; permute::Bool=true, scale::Bool=true, `sortby`) -> Matrix
```

Devuelve una matriz `M` cuyas columnas son los vectores propios de `A`. (El `k`-ésimo vector propio se puede obtener del corte `M[:, k]`.) Las palabras clave `permute`, `scale` y `sortby` son las mismas que para [`eigen`](@ref).

# Ejemplos

```jldoctest
julia> eigvecs([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```
