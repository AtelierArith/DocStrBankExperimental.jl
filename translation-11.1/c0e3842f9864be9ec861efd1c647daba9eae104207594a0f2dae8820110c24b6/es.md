```
permute!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti},
         p::AbstractVector{<:Integer}, q::AbstractVector{<:Integer},
         [C::AbstractSparseMatrixCSC{Tv,Ti}]) where {Tv,Ti}
```

Permuta bilateralmente `A`, almacenando el resultado `PAQ` (`A[p,q]`) en `X`. Almacena el resultado intermedio `(AQ)^T` (`transpose(A[:,q])`) en el argumento opcional `C` si está presente. Requiere que ninguno de `X`, `A`, y, si está presente, `C` se alias entre sí; para almacenar el resultado `PAQ` de vuelta en `A`, utiliza el siguiente método que no incluye `X`:

```
permute!(A::AbstractSparseMatrixCSC{Tv,Ti}, p::AbstractVector{<:Integer},
         q::AbstractVector{<:Integer}[, C::AbstractSparseMatrixCSC{Tv,Ti},
         [workcolptr::Vector{Ti}]]) where {Tv,Ti}
```

Las dimensiones de `X` deben coincidir con las de `A` (`size(X, 1) == size(A, 1)` y `size(X, 2) == size(A, 2)`), y `X` debe tener suficiente almacenamiento para acomodar todas las entradas asignadas en `A` (`length(rowvals(X)) >= nnz(A)` y `length(nonzeros(X)) >= nnz(A)`). La longitud de la permutación de columnas `q` debe coincidir con el conteo de columnas de `A` (`length(q) == size(A, 2)`). La longitud de la permutación de filas `p` debe coincidir con el conteo de filas de `A` (`length(p) == size(A, 1)`).

Las dimensiones de `C` deben coincidir con las de `transpose(A)` (`size(C, 1) == size(A, 2)` y `size(C, 2) == size(A, 1)`), y `C` debe tener suficiente almacenamiento para acomodar todas las entradas asignadas en `A` (`length(rowvals(C)) >= nnz(A)` y `length(nonzeros(C)) >= nnz(A)`).

Para información adicional (algorítmica), y para versiones de estos métodos que prescinden de la verificación de argumentos, consulta los métodos padres (no exportados) `unchecked_noalias_permute!` y `unchecked_aliasing_permute!`.

Consulta también [`permute`](@ref).
