```
inv(M)
```

Inverse de matrice. Calcule la matrice `N` telle que `M * N = I`, où `I` est la matrice identité. Calculé en résolvant la division à gauche `N = M \ I`.

# Exemples

```jldoctest
julia> M = [2 5; 1 3]
2×2 Matrix{Int64}:
 2  5
 1  3

julia> N = inv(M)
2×2 Matrix{Float64}:
  3.0  -5.0
 -1.0   2.0

julia> M*N == N*M == Matrix(I, 2, 2)
true
```
