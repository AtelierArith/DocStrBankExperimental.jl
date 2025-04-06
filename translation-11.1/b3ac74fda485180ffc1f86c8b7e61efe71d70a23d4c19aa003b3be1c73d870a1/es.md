```
vec(a::AbstractArray) -> AbstractVector
```

Reorganiza el arreglo `a` como un vector columna unidimensional. Devuelve `a` si ya es un `AbstractVector`. El arreglo resultante comparte los mismos datos subyacentes que `a`, por lo que solo será mutable si `a` es mutable, en cuyo caso modificar uno también modificará al otro.

# Ejemplos

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> vec(a)
6-element Vector{Int64}:
 1
 4
 2
 5
 3
 6

julia> vec(1:3)
1:3
```

Ver también [`reshape`](@ref), [`dropdims`](@ref).
