```
length(A::AbstractArray)
```

Devuelve el número de elementos en el array, por defecto es `prod(size(A))`.

# Ejemplos

```jldoctest
julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
