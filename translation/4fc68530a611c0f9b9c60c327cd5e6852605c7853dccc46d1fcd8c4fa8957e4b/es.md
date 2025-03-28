```
dropdims(A; dims)
```

Devuelve un array con los mismos datos que `A`, pero con las dimensiones especificadas por `dims` eliminadas. `size(A,d)` debe ser igual a 1 para cada `d` en `dims`, y se prohíben dimensiones repetidas o números fuera de `1:ndims(A)`.

El resultado comparte los mismos datos subyacentes que `A`, de modo que el resultado es mutable si y solo si `A` es mutable, y establecer elementos de uno altera los valores del otro.

Véase también: [`reshape`](@ref), [`vec`](@ref).

# Ejemplos

```jldoctest
julia> a = reshape(Vector(1:4),(2,2,1,1))
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

julia> b = dropdims(a; dims=3)
2×2×1 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

julia> b[1,1,1] = 5; a
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 5  3
 2  4
```
