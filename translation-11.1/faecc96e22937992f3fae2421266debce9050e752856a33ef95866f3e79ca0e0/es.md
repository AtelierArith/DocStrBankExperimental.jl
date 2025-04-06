```
resize!(a::Vector, n::Integer) -> Vector
```

Redimensiona `a` para contener `n` elementos. Si `n` es menor que la longitud actual de la colección, se conservarán los primeros `n` elementos. Si `n` es mayor, no se garantiza que los nuevos elementos estén inicializados.

# Ejemplos

```jldoctest
julia> resize!([6, 5, 4, 3, 2, 1], 3)
3-element Vector{Int64}:
 6
 5
 4

julia> a = resize!([6, 5, 4, 3, 2, 1], 8);

julia> length(a)
8

julia> a[1:6]
6-element Vector{Int64}:
 6
 5
 4
 3
 2
 1
```
