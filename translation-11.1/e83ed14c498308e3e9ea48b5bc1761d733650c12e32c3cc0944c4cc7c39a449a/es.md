```
sort(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Ordena un arreglo multidimensional `A` a lo largo de la dimensión dada. Consulta [`sort!`](@ref) para una descripción de los posibles argumentos de palabra clave.

Para ordenar secciones de un arreglo, consulta [`sortslices`](@ref).

# Ejemplos

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort(A, dims = 1)
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort(A, dims = 2)
2×2 Matrix{Int64}:
 3  4
 1  2
```
