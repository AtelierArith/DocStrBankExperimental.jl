```
sortperm(A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

Devuelve un vector o arreglo de permutación `I` que coloca `A[I]` en orden ascendente a lo largo de la dimensión dada. Si `A` tiene más de una dimensión, entonces el argumento de palabra clave `dims` debe ser especificado. El orden se especifica utilizando las mismas palabras clave que [`sort!`](@ref). La permutación está garantizada para ser estable incluso si el algoritmo de ordenamiento es inestable: los índices de elementos iguales aparecerán en orden ascendente.

Véase también [`sortperm!`](@ref), [`partialsortperm`](@ref), [`invperm`](@ref), [`indexin`](@ref). Para ordenar secciones de un arreglo, consulte [`sortslices`](@ref).

!!! compat "Julia 1.9"
    El método que acepta `dims` requiere al menos Julia 1.9.


# Ejemplos

```jldoctest
julia> v = [3, 1, 2];

julia> p = sortperm(v)
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]
2×2 Matrix{Int64}:
 8  7
 5  6

julia> sortperm(A, dims = 1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm(A, dims = 2)
2×2 Matrix{Int64}:
 3  1
 2  4
```
