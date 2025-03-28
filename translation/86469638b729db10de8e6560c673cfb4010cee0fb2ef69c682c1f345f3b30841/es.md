```
qr(A::SparseMatrixCSC; tol=_default_tol(A), ordering=ORDERING_DEFAULT) -> QRSparse
```

Calcula la factorización `QR` de una matriz dispersa `A`. Se utilizan permutaciones de filas y columnas que reducen el llenado de manera que `F.R = F.Q'*A[F.prow,F.pcol]`. La aplicación principal de este tipo es resolver problemas de mínimos cuadrados o subdeterminado con [`\`](@ref). La función llama a la biblioteca C SPQR[^ACM933].

!!! note
    `qr(A::SparseMatrixCSC)` utiliza la biblioteca SPQR que es parte de [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse). Dado que esta biblioteca solo admite matrices dispersas con elementos de tipo [`Float64`](@ref) o `ComplexF64`, a partir de Julia v1.4 `qr` convierte `A` en una copia que es de tipo `SparseMatrixCSC{Float64}` o `SparseMatrixCSC{ComplexF64}` según corresponda.


# Ejemplos

```jldoctest
julia> A = sparse([1,2,3,4], [1,1,2,2], [1.0,1.0,1.0,1.0])
4×2 SparseMatrixCSC{Float64, Int64} con 4 entradas almacenadas:
 1.0   ⋅
 1.0   ⋅
  ⋅   1.0
  ⋅   1.0

julia> qr(A)
SparseArrays.SPQR.QRSparse{Float64, Int64}
Factor Q:
4×4 SparseArrays.SPQR.QRSparseQ{Float64, Int64}
Factor R:
2×2 SparseMatrixCSC{Float64, Int64} con 2 entradas almacenadas:
 -1.41421    ⋅
   ⋅       -1.41421
Permutación de filas:
Vector de 4 elementos{Int64}:
 1
 3
 4
 2
Permutación de columnas:
Vector de 2 elementos{Int64}:
 1
 2
```

[^ACM933]: Foster, L. V., & Davis, T. A. (2013). Algoritmo 933: Cálculo confiable de rango numérico, bases de espacio nulo, soluciones de pseudoinversa y soluciones básicas utilizando SuitesparseQR. ACM Trans. Math. Softw., 40(1). [doi:10.1145/2513109.2513116](https://doi.org/10.1145/2513109.2513116)
