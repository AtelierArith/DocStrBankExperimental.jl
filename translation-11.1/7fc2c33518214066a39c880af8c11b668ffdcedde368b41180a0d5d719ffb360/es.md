```
mean(itr)
```

Calcule la media de todos los elementos en una colección.

!!! note
    Si `itr` contiene valores `NaN` o [`missing`](@ref), el resultado también es `NaN` o `missing` (`missing` tiene prioridad si el arreglo contiene ambos). Utilice la función [`skipmissing`](@ref) para omitir entradas `missing` y calcular la media de los valores no faltantes.


# Ejemplos

```jldoctest
julia> using Statistics

julia> mean(1:20)
10.5

julia> mean([1, missing, 3])
missing

julia> mean(skipmissing([1, missing, 3]))
2.0
```
