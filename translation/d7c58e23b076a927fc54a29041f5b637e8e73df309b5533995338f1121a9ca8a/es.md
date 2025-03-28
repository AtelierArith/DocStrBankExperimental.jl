```
sparse!(I::AbstractVector{Ti}, J::AbstractVector{Ti}, V::AbstractVector{Tv},
        m::Integer, n::Integer, combine, klasttouch::Vector{Ti},
        csrrowptr::Vector{Ti}, csrcolval::Vector{Ti}, csrnzval::Vector{Tv},
        [csccolptr::Vector{Ti}], [cscrowval::Vector{Ti}, cscnzval::Vector{Tv}] ) where {Tv,Ti<:Integer}
```

Padre y controlador experto para [`sparse`](@ref); consulte [`sparse`](@ref) para un uso básico. Este método permite al usuario proporcionar almacenamiento preasignado para los objetos intermedios y el resultado de `sparse` como se describe a continuación. Esta capacidad permite una construcción sucesiva más eficiente de [`SparseMatrixCSC`](@ref)s a partir de representaciones de coordenadas, y también permite la extracción de una representación de columna no ordenada de la transposición del resultado sin costo adicional.

Este método consta de tres pasos principales: (1) Ordenar por conteo la representación de coordenadas proporcionada en una forma CSR de fila no ordenada que incluye entradas repetidas. (2) Barrer a través de la forma CSR, calculando simultáneamente el arreglo de punteros de columna de la forma CSC deseada, detectando entradas repetidas y reempaquetando la forma CSR con entradas repetidas combinadas; esta etapa produce una forma CSR de fila no ordenada sin entradas repetidas. (3) Ordenar por conteo la forma CSR anterior en una forma CSC completamente ordenada sin entradas repetidas.

Los arreglos de entrada `csrrowptr`, `csrcolval` y `csrnzval` constituyen almacenamiento para las formas CSR intermedias y requieren `length(csrrowptr) >= m + 1`, `length(csrcolval) >= length(I)`, y `length(csrnzval >= length(I))`. El arreglo de entrada `klasttouch`, espacio de trabajo para la segunda etapa, requiere `length(klasttouch) >= n`. Los arreglos de entrada opcionales `csccolptr`, `cscrowval` y `cscnzval` constituyen almacenamiento para la forma CSC devuelta `S`. Si es necesario, estos se redimensionan automáticamente para satisfacer `length(csccolptr) = n + 1`, `length(cscrowval) = nnz(S)` y `length(cscnzval) = nnz(S)`; por lo tanto, si `nnz(S)` es desconocido desde el principio, pasar vectores vacíos del tipo apropiado (`Vector{Ti}()` y `Vector{Tv}()` respectivamente) es suficiente, o llamar al método `sparse!` descuidando `cscrowval` y `cscnzval`.

Al regresar, `csrrowptr`, `csrcolval` y `csrnzval` contienen una representación de columna no ordenada de la transposición del resultado.

Puede reutilizar el almacenamiento de los arreglos de entrada (`I`, `J`, `V`) para los arreglos de salida (`csccolptr`, `cscrowval`, `cscnzval`). Por ejemplo, puede llamar a `sparse!(I, J, V, csrrowptr, csrcolval, csrnzval, I, J, V)`. Tenga en cuenta que se redimensionarán para satisfacer las condiciones anteriores.

Por razones de eficiencia, este método no realiza comprobaciones de argumentos más allá de `1 <= I[k] <= m` y `1 <= J[k] <= n`. Úselo con cuidado. Es recomendable probar con `--check-bounds=yes`.

Este método se ejecuta en tiempo `O(m, n, length(I))`. El algoritmo HALFPERM descrito en F. Gustavson, "Dos algoritmos rápidos para matrices dispersas: multiplicación y transposición permutada," ACM TOMS 4(3), 250-269 (1978) inspiró el uso de un par de ordenamientos por conteo en este método.
