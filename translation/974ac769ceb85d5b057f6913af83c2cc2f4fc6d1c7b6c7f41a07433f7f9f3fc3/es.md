```
median(itr)
```

Calcule la mediana de todos los elementos en una colección. Para un número par de elementos, no existe un elemento de mediana exacto, por lo que el resultado es equivalente a calcular la media de dos elementos de mediana.

!!! nota
    Si `itr` contiene valores `NaN` o [`missing`](@ref), el resultado también es `NaN` o `missing` (`missing` tiene prioridad si `itr` contiene ambos). Utilice la función [`skipmissing`](@ref) para omitir entradas `missing` y calcular la mediana de los valores no faltantes.


# Ejemplos

```jldoctest
julia> using Statistics

julia> median([1, 2, 3])
2.0

julia> median([1, 2, 3, 4])
2.5

julia> median([1, 2, missing, 4])
missing

julia> median(skipmissing([1, 2, missing, 4]))
2.0
```
