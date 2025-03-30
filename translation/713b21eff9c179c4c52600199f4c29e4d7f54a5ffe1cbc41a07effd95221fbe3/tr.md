```
A / B
```

Matris sağ-bölümü: `A / B`, `(B' \ A')'` ile eşdeğerdir; burada [`\`](@ref) sol-bölüm operatörüdür. Kare matrisler için, sonuç `X` öyle ki `A == X*B` olur.

Ayrıca bakınız: [`rdiv!`](@ref).

# Örnekler

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
