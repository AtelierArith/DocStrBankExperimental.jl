```
A / B
```

División a la derecha de matrices: `A / B` es equivalente a `(B' \ A')'` donde [`\`](@ref) es el operador de división a la izquierda. Para matrices cuadradas, el resultado `X` es tal que `A == X*B`.

Véase también: [`rdiv!`](@ref).

# Ejemplos

```jldoctest
julia> A = Float64[1 4 5; 3 9 2]; B = Float64[1 4 2; 3 4 2; 8 7 1];

julia> X = A / B
2×3 Matrix{Float64}:
 -0.65   3.75  -1.2
  3.25  -2.75   1.0

julia> isapprox(A, X*B)
true

julia> isapprox(X, A*pinv(B))
true
```
