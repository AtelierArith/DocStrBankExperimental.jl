```
var(itr; corrected::Bool=true, mean=nothing[, dims])
```

Calcula la varianza muestral de la colección `itr`.

El algoritmo devuelve un estimador de la varianza de la distribución generativa bajo la suposición de que cada entrada de `itr` es una muestra extraída de la misma distribución desconocida, con las muestras no correlacionadas. Para arreglos, este cálculo es equivalente a calcular `sum((itr .- mean(itr)).^2) / (length(itr) - 1)`. Si `corrected` es `true`, entonces la suma se escala con `n-1`, mientras que la suma se escala con `n` si `corrected` es `false`, donde `n` es el número de elementos en `itr`.

Si `itr` es un `AbstractArray`, se pueden proporcionar `dims` para calcular la varianza sobre dimensiones.

Se puede proporcionar un `mean` precomputado. Cuando se especifica `dims`, `mean` debe ser un arreglo con la misma forma que `mean(itr, dims=dims)` (se permiten dimensiones singleton adicionales al final).

!!! note
    Si el arreglo contiene valores `NaN` o [`missing`](@ref), el resultado también es `NaN` o `missing` (`missing` tiene prioridad si el arreglo contiene ambos). Usa la función [`skipmissing`](@ref) para omitir entradas `missing` y calcular la varianza de los valores no faltantes.

