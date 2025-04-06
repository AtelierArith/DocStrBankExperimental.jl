```
BitArray{N} <: AbstractArray{Bool, N}
```

Arreglo booleano `N`-dimensional eficiente en espacio, utilizando solo un bit para cada valor booleano.

Los `BitArray` empaquetan hasta 64 valores en cada 8 bytes, resultando en una eficiencia de espacio de 8x sobre `Array{Bool, N}` y permitiendo que algunas operaciones trabajen en 64 valores a la vez.

Por defecto, Julia devuelve `BitArrays` de operaciones de [broadcasting](@ref Broadcasting) que generan elementos booleanos (incluyendo comparaciones con punto como `.==`) así como de las funciones [`trues`](@ref) y [`falses`](@ref).

!!! note
    Debido a su formato de almacenamiento empaquetado, el acceso concurrente a los elementos de un `BitArray` donde al menos uno de ellos es una escritura no es seguro para hilos.

