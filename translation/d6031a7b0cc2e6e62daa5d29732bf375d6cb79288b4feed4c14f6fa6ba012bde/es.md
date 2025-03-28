```
minimum(f, A::AbstractArray; dims)
```

Calcule el valor mínimo llamando a la función `f` en cada elemento de un array sobre las dimensiones dadas.

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum(abs2, A, dims=1)
1×2 Matrix{Int64}:
 1  4

julia> minimum(abs2, A, dims=2)
2×1 Matrix{Int64}:
 1
 9
```
