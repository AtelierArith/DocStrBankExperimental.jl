```
sort!(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Ordena el arreglo multidimensional `A` a lo largo de la dimensión `dims`. Consulta la versión unidimensional de [`sort!`](@ref) para una descripción de los posibles argumentos de palabra clave.

Para ordenar secciones de un arreglo, consulta [`sortslices`](@ref).

!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.


# Ejemplos

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort!(A, dims = 1); A
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort!(A, dims = 2); A
2×2 Matrix{Int64}:
 1  2
 3  4
```
