```
LU <: Factorización
```

Tipo de factorización de matriz de la factorización `LU` de una matriz cuadrada `A`. Este es el tipo de retorno de [`lu`](@ref), la función de factorización de matriz correspondiente.

Los componentes individuales de la factorización `F::LU` se pueden acceder a través de [`getproperty`](@ref):

| Componente | Descripción                                      |
|:---------- |:------------------------------------------------ |
| `F.L`      | Parte `L` (triangular inferior unitario) de `LU` |
| `F.U`      | Parte `U` (triangular superior) de `LU`          |
| `F.p`      | Permutación `Vector` (derecha)                   |
| `F.P`      | Permutación `Matrix` (derecha)                   |

Iterar sobre la factorización produce los componentes `F.L`, `F.U` y `F.p`.

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
```
