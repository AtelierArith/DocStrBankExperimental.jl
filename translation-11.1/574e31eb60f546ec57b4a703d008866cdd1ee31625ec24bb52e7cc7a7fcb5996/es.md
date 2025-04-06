```
cholesky(A::SparseMatrixCSC; shift = 0.0, check = true, perm = nothing) -> CHOLMOD.Factor
```

Calcula la factorización de Cholesky de una matriz dispersa definida positiva `A`. `A` debe ser una [`SparseMatrixCSC`](@ref) o una vista [`Symmetric`](@ref)/[`Hermitian`](@ref) de una `SparseMatrixCSC`. Ten en cuenta que incluso si `A` no tiene la etiqueta de tipo, aún debe ser simétrica o hermítica. Si no se proporciona `perm`, se utiliza una permutación que reduce el llenado. `F = cholesky(A)` se usa con mayor frecuencia para resolver sistemas de ecuaciones con `F\b`, pero también se definen los métodos [`diag`](@ref), [`det`](@ref) y [`logdet`](@ref) para `F`. También puedes extraer factores individuales de `F`, usando `F.L`. Sin embargo, dado que el pivoteo está activado por defecto, la factorización se representa internamente como `A == P'*L*L'*P` con una matriz de permutación `P`; usar solo `L` sin tener en cuenta `P` dará respuestas incorrectas. Para incluir los efectos de la permutación, es preferible extraer factores "combinados" como `PtL = F.PtL` (el equivalente de `P'*L`) y `LtP = F.UP` (el equivalente de `L'*P`).

Cuando `check = true`, se lanza un error si la descomposición falla. Cuando `check = false`, la responsabilidad de verificar la validez de la descomposición (a través de [`issuccess`](@ref)) recae en el usuario.

Establecer el argumento de palabra clave opcional `shift` calcula la factorización de `A+shift*I` en lugar de `A`. Si se proporciona el argumento `perm`, debe ser una permutación de `1:size(A,1)` que da el orden a utilizar (en lugar del orden AMD predeterminado de CHOLMOD).

# Ejemplos

En el siguiente ejemplo, la permutación que reduce el llenado utilizada es `[3, 2, 1]`. Si `perm` se establece en `1:3` para forzar ninguna permutación, el número de elementos no nulos en el factor es 6.

```jldoctest
julia> A = [2 1 1; 1 2 0; 1 0 2]
3×3 Matrix{Int64}:
 2  1  1
 1  2  0
 1  0  2

julia> C = cholesky(sparse(A))
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  5
nnz:     5
success: true

julia> C.p
3-element Vector{Int64}:
 3
 2
 1

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421   0.0       0.0
 0.0       1.41421   0.0
 0.707107  0.707107  1.0

julia> L * L' ≈ A[C.p, C.p]
true

julia> P = sparse(1:3, C.p, ones(3))
3×3 SparseMatrixCSC{Float64, Int64} con 3 entradas almacenadas:
  ⋅    ⋅   1.0
  ⋅   1.0   ⋅
 1.0   ⋅    ⋅

julia> P' * L * L' * P ≈ A
true

julia> C = cholesky(sparse(A), perm=1:3)
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  6
nnz:     6
success: true

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421    0.0       0.0
 0.707107   1.22474   0.0
 0.707107  -0.408248  1.1547

julia> L * L' ≈ A
true
```

!!! nota
    Este método utiliza la biblioteca CHOLMOD[^ACM887][^DavisHager2009] de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). CHOLMOD solo admite tipos reales o complejos en precisión simple o doble. Las matrices de entrada que no son de esos tipos de elementos se convertirán a estos tipos según sea apropiado.

    Muchas otras funciones de CHOLMOD están envueltas pero no exportadas del módulo `Base.SparseArrays.CHOLMOD`.


[^ACM887]: Chen, Y., Davis, T. A., Hager, W. W., & Rajamanickam, S. (2008). Algoritmo 887: CHOLMOD, Factorización de Cholesky dispersa supernodal y actualización/bajada. ACM Trans. Math. Softw., 35(3). [doi:10.1145/1391989.1391995](https://doi.org/10.1145/1391989.1391995)

[^DavisHager2009]: Davis, Timothy A., & Hager, W. W. (2009). Supernodos dinámicos en la actualización/bajada de Cholesky dispersa y soluciones triangulares. ACM Trans. Math. Softw., 35(4). [doi:10.1145/1462173.1462176](https://doi.org/10.1145/1462173.1462176)
