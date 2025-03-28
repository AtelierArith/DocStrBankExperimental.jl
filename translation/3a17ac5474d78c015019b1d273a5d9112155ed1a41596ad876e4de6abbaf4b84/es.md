```
Simétrico(A::AbstractMatrix, uplo::Symbol=:U)
```

Construye una vista `Simétrico` del triángulo superior (si `uplo = :U`) o inferior (si `uplo = :L`) de la matriz `A`.

Las vistas `Simétrico` son principalmente útiles para matrices simétricas reales, para las cuales se habilitan algoritmos especializados (por ejemplo, para problemas de autovalores) para los tipos `Simétrico`. Más generalmente, véase también [`Hermitiano(A)`](@ref) para matrices hermitianas `A == A'`, que es efectivamente equivalente a `Simétrico` para matrices reales, pero también es útil para matrices complejas. (Mientras que las matrices `Simétrico` complejas son compatibles, tienen pocos o ningún algoritmo especializado).

Para calcular la parte simétrica de una matriz real, o más generalmente la parte hermitiana `(A + A') / 2` de una matriz real o compleja `A`, use [`hermitianpart`](@ref).

# Ejemplos

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> Supper = Simétrico(A)
3×3 Simétrico{Int64, Matrix{Int64}}:
 1  2  3
 2  5  6
 3  6  9

julia> Slower = Simétrico(A, :L)
3×3 Simétrico{Int64, Matrix{Int64}}:
 1  4  7
 4  5  8
 7  8  9

julia> hermitianpart(A)
3×3 Hermitiano{Float64, Matrix{Float64}}:
 1.0  3.0  5.0
 3.0  5.0  7.0
 5.0  7.0  9.0
```

Tenga en cuenta que `Supper` no será igual a `Slower` a menos que `A` sea simétrica (por ejemplo, si `A == transpose(A)`).
