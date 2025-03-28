```
A / B
```

La division à droite des matrices : `A / B` est équivalente à `(B' \ A')'` où [`\`](@ref) est l'opérateur de division à gauche. Pour les matrices carrées, le résultat `X` est tel que `A == X*B`.

Voir aussi : [`rdiv!`](@ref).

# Exemples

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
