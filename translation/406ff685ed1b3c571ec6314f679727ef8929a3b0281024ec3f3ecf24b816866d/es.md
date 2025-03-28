```
CartesianIndex(i, j, k...)   -> I
CartesianIndex((i, j, k...)) -> I
```

Crea un índice multidimensional `I`, que se puede usar para indexar un arreglo multidimensional `A`. En particular, `A[I]` es equivalente a `A[i,j,k...]`. Se pueden mezclar libremente índices enteros y `CartesianIndex`; por ejemplo, `A[Ipre, i, Ipost]` (donde `Ipre` y `Ipost` son índices `CartesianIndex` y `i` es un `Int`) puede ser una expresión útil al escribir algoritmos que funcionan a lo largo de una sola dimensión de un arreglo de dimensionalidad arbitraria.

Un `CartesianIndex` a veces es producido por [`eachindex`](@ref), y siempre cuando se itera con un [`CartesianIndices`](@ref) explícito.

Un `I::CartesianIndex` se trata como un "escalar" (no un contenedor) para `broadcast`. Para iterar sobre los componentes de un `CartesianIndex`, conviértelo en una tupla con `Tuple(I)`.

# Ejemplos

```jldoctest
julia> A = reshape(Vector(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[CartesianIndex((1, 1, 1, 1))]
1

julia> A[CartesianIndex((1, 1, 1, 2))]
9

julia> A[CartesianIndex((1, 1, 2, 1))]
5
```

!!! compat "Julia 1.10"
    Usar un `CartesianIndex` como un "escalar" para `broadcast` requiere Julia 1.10; en versiones anteriores, usa `Ref(I)`.

