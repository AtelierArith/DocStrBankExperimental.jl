```
length(collection) -> Integer
```

Devuelve el número de elementos en la colección.

Usa [`lastindex`](@ref) para obtener el último índice válido de una colección indexable.

Ver también: [`size`](@ref), [`ndims`](@ref), [`eachindex`](@ref).

# Ejemplos

```jldoctest
julia> length(1:5)
5

julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
