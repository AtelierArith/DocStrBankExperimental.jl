```
stdm(itr, mean; corrected::Bool=true[, dims])
```

Calcula la desviación estándar muestral de la colección `itr`, con la(s) media(s) conocida(s) `mean`.

El algoritmo devuelve un estimador de la desviación estándar de la distribución generativa bajo la suposición de que cada entrada de `itr` es una muestra extraída de la misma distribución desconocida, con las muestras no correlacionadas. Para arreglos, este cálculo es equivalente a calcular `sqrt(sum((itr .- mean(itr)).^2) / (length(itr) - 1))`. Si `corrected` es `true`, entonces la suma se escala con `n-1`, mientras que la suma se escala con `n` si `corrected` es `false`, siendo `n` el número de elementos en `itr`.

Si `itr` es un `AbstractArray`, se pueden proporcionar `dims` para calcular la desviación estándar sobre dimensiones. En ese caso, `mean` debe ser un arreglo con la misma forma que `mean(itr, dims=dims)` (se permiten dimensiones singleton adicionales al final).

!!! note
    Si el arreglo contiene valores `NaN` o [`missing`](@ref), el resultado también es `NaN` o `missing` (`missing` tiene prioridad si el arreglo contiene ambos). Usa la función [`skipmissing`](@ref) para omitir entradas `missing` y calcular la desviación estándar de los valores no faltantes.

