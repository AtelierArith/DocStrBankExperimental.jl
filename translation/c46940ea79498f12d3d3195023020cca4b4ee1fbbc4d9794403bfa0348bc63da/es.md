```
sortslices(A; dims, alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

Ordena las secciones de un arreglo `A`. El argumento clave requerido `dims` debe ser un entero o una tupla de enteros. Especifica la(s) dimensión(es) sobre las que se ordenan las secciones.

Por ejemplo, si `A` es una matriz, `dims=1` ordenará las filas, `dims=2` ordenará las columnas. Ten en cuenta que la función de comparación predeterminada en secciones unidimensionales ordena lexicográficamente.

Para los demás argumentos clave, consulta la documentación de [`sort!`](@ref).

# Ejemplos

```jldoctest
julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1) # Ordenar filas
3×3 Matrix{Int64}:
 -1   6  4
  7   3  5
  9  -2  8

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; -1 6 4; 9 -2 8], dims=1, rev=true)
3×3 Matrix{Int64}:
  9  -2  8
  7   3  5
 -1   6  4

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2) # Ordenar columnas
3×3 Matrix{Int64}:
  3   5  7
 -1  -4  6
 -2   8  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, alg=InsertionSort, lt=(x,y)->isless(x[2],y[2]))
3×3 Matrix{Int64}:
  5   3  7
 -4  -1  6
  8  -2  9

julia> sortslices([7 3 5; 6 -1 -4; 9 -2 8], dims=2, rev=true)
3×3 Matrix{Int64}:
 7   5   3
 6  -4  -1
 9   8  -2
```

# Dimensiones superiores

`sortslices` se extiende naturalmente a dimensiones superiores. Por ejemplo, si `A` es un arreglo de 2x2x2, `sortslices(A, dims=3)` ordenará las secciones dentro de la 3ª dimensión, pasando las secciones de 2x2 `A[:, :, 1]` y `A[:, :, 2]` a la función de comparación. Ten en cuenta que, aunque no hay un orden predeterminado en secciones de dimensiones superiores, puedes usar el argumento clave `by` o `lt` para especificar dicho orden.

Si `dims` es una tupla, el orden de las dimensiones en `dims` es relevante y especifica el orden lineal de las secciones. Por ejemplo, si `A` es tridimensional y `dims` es `(1, 2)`, los ordenamientos de las dos primeras dimensiones se reorganizan de tal manera que las secciones (de la tercera dimensión restante) se ordenan. Si `dims` es `(2, 1)` en su lugar, se tomarán las mismas secciones, pero el orden del resultado será en orden por filas.

# Ejemplos de dimensiones superiores

```
julia> A = [4 3; 2 1 ;;; 'A' 'B'; 'C' 'D']
2×2×2 Array{Any, 3}:
[:, :, 1] =
 4  3
 2  1

[:, :, 2] =
 'A'  'B'
 'C'  'D'

julia> sortslices(A, dims=(1,2))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 'D'  'B'
 'C'  'A'

julia> sortslices(A, dims=(2,1))
2×2×2 Array{Any, 3}:
[:, :, 1] =
 1  2
 3  4

[:, :, 2] =
 'D'  'C'
 'B'  'A'

julia> sortslices(reshape([5; 4; 3; 2; 1], (1,1,5)), dims=3, by=x->x[1,1])
1×1×5 Array{Int64, 3}:
[:, :, 1] =
 1

[:, :, 2] =
 2

[:, :, 3] =
 3

[:, :, 4] =
 4

[:, :, 5] =
 5
```
