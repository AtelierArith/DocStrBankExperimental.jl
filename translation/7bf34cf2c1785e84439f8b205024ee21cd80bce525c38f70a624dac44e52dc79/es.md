```
lu(A, pivot = RowMaximum(); check = true, allowsingular = false) -> F::LU
```

Calcula la factorización LU de `A`.

Cuando `check = true`, se lanza un error si la descomposición falla. Cuando `check = false`, la responsabilidad de verificar la validez de la descomposición (a través de [`issuccess`](@ref)) recae en el usuario.

Por defecto, con `check = true`, también se lanza un error cuando la descomposición produce factores válidos, pero el factor triangular superior `U` es deficiente en rango. Esto se puede cambiar pasando `allowsingular = true`.

En la mayoría de los casos, si `A` es un subtipo `S` de `AbstractMatrix{T}` con un tipo de elemento `T` que soporta `+`, `-`, `*` y `/`, el tipo de retorno es `LU{T,S{T}}`.

En general, la factorización LU implica una permutación de las filas de la matriz (correspondiente a la salida `F.p` descrita a continuación), conocida como "pivoting" (porque corresponde a elegir qué fila contiene el "pivot", la entrada diagonal de `F.U`). Una de las siguientes estrategias de pivoting se puede seleccionar a través del argumento opcional `pivot`:

  * `RowMaximum()` (por defecto): la estrategia de pivoting estándar; el pivot corresponde al elemento de valor absoluto máximo entre las filas restantes a factorizar. Esta estrategia de pivoting requiere que el tipo de elemento también soporte [`abs`](@ref) y [`<`](@ref). (Esta es generalmente la única opción numéricamente estable para matrices de punto flotante.)
  * `RowNonZero()`: el pivot corresponde al primer elemento no cero entre las filas restantes a factorizar. (Esto corresponde a la elección típica en cálculos manuales, y también es útil para tipos de números algebraicos más generales que soportan [`iszero`](@ref) pero no `abs` o `<`.)
  * `NoPivot()`: pivoting desactivado (fallará si se encuentra una entrada cero en una posición de pivot, incluso cuando `allowsingular = true`).

Los componentes individuales de la factorización `F` se pueden acceder a través de [`getproperty`](@ref):

| Componente | Descripción                             |
|:---------- |:--------------------------------------- |
| `F.L`      | `L` (parte triangular inferior) de `LU` |
| `F.U`      | `U` (parte triangular superior) de `LU` |
| `F.p`      | Permutación `Vector` (derecha)          |
| `F.P`      | Permutación `Matrix` (derecha)          |

Iterar sobre la factorización produce los componentes `F.L`, `F.U` y `F.p`.

La relación entre `F` y `A` es

`F.L*F.U == A[F.p, :]`

`F` además soporta las siguientes funciones:

| Función soportada   | `LU` | `LU{T,Tridiagonal{T}}` |
|:------------------- |:---- |:---------------------- |
| [`/`](@ref)         | ✓    |                        |
| [`\`](@ref)         | ✓    | ✓                      |
| [`inv`](@ref)       | ✓    | ✓                      |
| [`det`](@ref)       | ✓    | ✓                      |
| [`logdet`](@ref)    | ✓    | ✓                      |
| [`logabsdet`](@ref) | ✓    | ✓                      |
| [`size`](@ref)      | ✓    | ✓                      |

!!! compat "Julia 1.11"
    El argumento de palabra clave `allowsingular` se agregó en Julia 1.11.


# Ejemplos

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # desestructuración a través de la iteración

julia> l == F.L && u == F.U && p == F.p
true

julia> lu([1 2; 1 2], allowsingular = true)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0  0.0
 1.0  1.0
U factor (deficiente en rango):
2×2 Matrix{Float64}:
 1.0  2.0
 0.0  0.0
```
