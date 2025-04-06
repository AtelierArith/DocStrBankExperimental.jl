```
factorizar(A)
```

Calcula una factorización conveniente de `A`, basada en el tipo de la matriz de entrada. `factorizar` verifica `A` para ver si es simétrica/triangular/etc. si `A` se pasa como una matriz genérica. `factorizar` revisa cada elemento de `A` para verificar/desestimar cada propiedad. Se detendrá tan pronto como pueda descartar la simetría/estructura triangular. El valor de retorno se puede reutilizar para resolver de manera eficiente múltiples sistemas. Por ejemplo: `A=factorizar(A); x=A\b; y=A\C`.

| Propiedades de `A`         | tipo de factorización                      |
|:-------------------------- |:------------------------------------------ |
| Positivo-definido          | Cholesky (ver [`cholesky`](@ref))          |
| Densa Simétrica/Hermítica  | Bunch-Kaufman (ver [`bunchkaufman`](@ref)) |
| Escasa Simétrica/Hermítica | LDLt (ver [`ldlt`](@ref))                  |
| Triangular                 | Triangular                                 |
| Diagonal                   | Diagonal                                   |
| Bidiagonal                 | Bidiagonal                                 |
| Tridiagonal                | LU (ver [`lu`](@ref))                      |
| Tridiagonal real simétrica | LDLt (ver [`ldlt`](@ref))                  |
| Cuadrada general           | LU (ver [`lu`](@ref))                      |
| No cuadrada general        | QR (ver [`qr`](@ref))                      |

Si `factorizar` se llama en una matriz hermítica positiva-definida, por ejemplo, entonces `factorizar` devolverá una factorización de Cholesky.

# Ejemplos

```jldoctest
julia> A = Array(Bidiagonal(fill(1.0, (5, 5)), :U))
5×5 Matrix{Float64}:
 1.0  1.0  0.0  0.0  0.0
 0.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  1.0  1.0
 0.0  0.0  0.0  0.0  1.0

julia> factorizar(A) # factorizar verificará si A ya está factorizada
5×5 Bidiagonal{Float64, Vector{Float64}}:
 1.0  1.0   ⋅    ⋅    ⋅
  ⋅   1.0  1.0   ⋅    ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅    ⋅   1.0
```

Esto devuelve un `5×5 Bidiagonal{Float64}`, que ahora se puede pasar a otras funciones de álgebra lineal (por ejemplo, solucionadores de eigenvalores) que utilizarán métodos especializados para tipos `Bidiagonal`.
