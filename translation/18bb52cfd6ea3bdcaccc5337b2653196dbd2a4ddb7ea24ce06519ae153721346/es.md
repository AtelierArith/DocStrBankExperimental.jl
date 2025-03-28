```
keys(a::AbstractArray)
```

Devuelve un array eficiente que describe todos los índices válidos para `a` dispuestos en la forma de `a` misma.

Las claves de los arrays unidimensionales (vectores) son enteros, mientras que todos los demás arrays N-dimensionales utilizan [`CartesianIndex`](@ref) para describir sus ubicaciones. A menudo, los tipos de array especiales [`LinearIndices`](@ref) y [`CartesianIndices`](@ref) se utilizan para representar de manera eficiente estos arrays de enteros y `CartesianIndex`es, respectivamente.

Ten en cuenta que las `keys` de un array pueden no ser el tipo de índice más eficiente; para un rendimiento máximo utiliza [`eachindex`](@ref) en su lugar.

# Ejemplos

```jldoctest
julia> keys([4, 5, 6])
3-element LinearIndices{1, Tuple{Base.OneTo{Int64}}}:
 1
 2
 3

julia> keys([4 5; 6 7])
CartesianIndices((2, 2))
```
