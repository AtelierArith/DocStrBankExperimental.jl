```
UpperHessenberg(A::AbstractMatrix)
```

Construye una vista `UpperHessenberg` de la matriz `A`. Las entradas de `A` por debajo de la primera subdiagonal son ignoradas.

!!! compat "Julia 1.3"
    Este tipo fue añadido en Julia 1.3.


Se implementan algoritmos eficientes para `H \ b`, `det(H)`, y similares.

Consulta también la función [`hessenberg`](@ref) para factorizar cualquier matriz en una matriz superior de Hessenberg similar.

Si `F::Hessenberg` es el objeto de factorización, la matriz unitaria se puede acceder con `F.Q` y la matriz de Hessenberg con `F.H`. Cuando se extrae `Q`, el tipo resultante es el objeto `HessenbergQ`, y puede ser convertido a una matriz regular con [`convert(Array, _)`](@ref) (o `Array(_)` para abreviar).

Iterar la descomposición produce los factores `F.Q` y `F.H`.

# Ejemplos

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
4×4 Matrix{Int64}:
  1   2   3   4
  5   6   7   8
  9  10  11  12
 13  14  15  16

julia> UpperHessenberg(A)
4×4 UpperHessenberg{Int64, Matrix{Int64}}:
 1   2   3   4
 5   6   7   8
 ⋅  10  11  12
 ⋅   ⋅  15  16
```
