```
qr(A, pivot = NoPivot(); blocksize) -> F
```

Calcula la factorización QR de la matriz `A`: una matriz ortogonal (o unitaria si `A` es de valor complejo) `Q`, y una matriz triangular superior `R` tal que

$$
A = Q R
$$

El objeto devuelto `F` almacena la factorización en un formato empaquetado:

  * si `pivot == ColumnNorm()` entonces `F` es un objeto [`QRPivoted`](@ref),
  * de lo contrario, si el tipo de elemento de `A` es un tipo BLAS ([`Float32`](@ref), [`Float64`](@ref), `ComplexF32` o `ComplexF64`), entonces `F` es un objeto [`QRCompactWY`](@ref),
  * de lo contrario, `F` es un objeto [`QR`](@ref).

Los componentes individuales de la descomposición `F` se pueden recuperar a través de accesores de propiedades:

  * `F.Q`: la matriz ortogonal/unitaria `Q`
  * `F.R`: la matriz triangular superior `R`
  * `F.p`: el vector de permutación del pivote ([`QRPivoted`](@ref) solo)
  * `F.P`: la matriz de permutación del pivote ([`QRPivoted`](@ref) solo)

!!! note
    Cada referencia al factor triangular superior a través de `F.R` asigna un nuevo arreglo. Por lo tanto, es aconsejable almacenar ese arreglo, digamos, con `R = F.R` y continuar trabajando con `R`.


Iterar la descomposición produce los componentes `Q`, `R`, y si existe `p`.

Las siguientes funciones están disponibles para los objetos `QR`: [`inv`](@ref), [`size`](@ref), y [`\`](@ref). Cuando `A` es rectangular, `\` devolverá una solución de mínimos cuadrados y si la solución no es única, se devuelve la que tiene la norma más pequeña. Cuando `A` no tiene rango completo, se requiere la factorización con pivoteo (por columna) para obtener una solución de norma mínima.

Se permite la multiplicación con respecto a `Q` completo/cuadrado o no completo/cuadrado, es decir, tanto `F.Q*F.R` como `F.Q*A` son compatibles. Una matriz `Q` se puede convertir en una matriz regular con [`Matrix`](@ref). Esta operación devuelve el factor Q "delgado", es decir, si `A` es `m`×`n` con `m>=n`, entonces `Matrix(F.Q)` produce una matriz `m`×`n` con columnas ortonormales. Para recuperar el factor Q "completo", una matriz ortogonal `m`×`m`, usa `F.Q*I` o `collect(F.Q)`. Si `m<=n`, entonces `Matrix(F.Q)` produce una matriz ortogonal `m`×`m`.

El tamaño del bloque para la descomposición QR se puede especificar mediante el argumento de palabra clave `blocksize :: Integer` cuando `pivot == NoPivot()` y `A isa StridedMatrix{<:BlasFloat}`. Se ignora cuando `blocksize > minimum(size(A))`. Ver [`QRCompactWY`](@ref).

!!! compat "Julia 1.4"
    El argumento de palabra clave `blocksize` requiere Julia 1.4 o posterior.


# Ejemplos

```jldoctest
julia> A = [3.0 -6.0; 4.0 -8.0; 0.0 1.0]
3×2 Matrix{Float64}:
 3.0  -6.0
 4.0  -8.0
 0.0   1.0

julia> F = qr(A)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Factor Q: 3×3 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
Factor R:
2×2 Matrix{Float64}:
 -5.0  10.0
  0.0  -1.0

julia> F.Q * F.R == A
true
```

!!! note
    `qr` devuelve múltiples tipos porque LAPACK utiliza varias representaciones que minimizan los requisitos de almacenamiento de memoria de los productos de reflectores elementales de Householder, de modo que las matrices `Q` y `R` se pueden almacenar de manera compacta en lugar de como dos matrices densas separadas.

