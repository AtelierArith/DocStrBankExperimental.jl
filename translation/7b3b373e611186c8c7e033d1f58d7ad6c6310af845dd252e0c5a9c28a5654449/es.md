```
halfperm!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{TvA,Ti},
          q::AbstractVector{<:Integer}, f::Function = identity) where {Tv,TvA,Ti}
```

Permuta y transpone `A`, aplicando simultáneamente `f` a cada entrada de `A`, almacenando el resultado `(f(A)Q)^T` (`map(f, transpose(A[:,q]))`) en `X`.

El tipo de elemento `Tv` de `X` debe coincidir con `f(::TvA)`, donde `TvA` es el tipo de elemento de `A`. Las dimensiones de `X` deben coincidir con las de `transpose(A)` (`size(X, 1) == size(A, 2)` y `size(X, 2) == size(A, 1)`), y `X` debe tener suficiente almacenamiento para acomodar todas las entradas asignadas en `A` (`length(rowvals(X)) >= nnz(A)` y `length(nonzeros(X)) >= nnz(A)`). La longitud de la permutación de columna `q` debe coincidir con el conteo de columnas de `A` (`length(q) == size(A, 2)`).

Este método es el padre de varios métodos que realizan operaciones de transposición y permutación en [`SparseMatrixCSC`](@ref)s. Dado que este método no realiza ninguna verificación de argumentos, se prefiere el uso de los métodos hijos más seguros (`[c]transpose[!]`, `permute[!]`) en lugar de su uso directo.

Este método implementa el algoritmo `HALFPERM` descrito en F. Gustavson, "Dos algoritmos rápidos para matrices dispersas: multiplicación y transposición permutada," ACM TOMS 4(3), 250-269 (1978). El algoritmo se ejecuta en tiempo `O(size(A, 1), size(A, 2), nnz(A))` y no requiere espacio más allá del que se pasa.
