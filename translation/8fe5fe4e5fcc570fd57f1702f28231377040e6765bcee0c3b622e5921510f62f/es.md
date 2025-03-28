```
muladd(x, y, z)
```

Multiplicación-suma combinada: calcula `x*y+z`, pero permite que la suma y la multiplicación se fusionen entre sí o con operaciones circundantes para mejorar el rendimiento. Por ejemplo, esto puede implementarse como un [`fma`](@ref) si el hardware lo admite de manera eficiente. El resultado puede ser diferente en diferentes máquinas y también puede ser diferente en la misma máquina debido a la propagación de constantes u otras optimizaciones. Ver [`fma`](@ref).

# Ejemplos

```jldoctest
julia> muladd(3, 2, 1)
7

julia> 3 * 2 + 1
7
```
