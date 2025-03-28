```
lyap(A, C)
```

Calcule la solution `X` de l'équation de Lyapunov continue `AX + XA' + C = 0`, où aucun eigenvalue de `A` n'a de partie réelle nulle et aucun deux eigenvalues ne sont des conjugués complexes négatifs l'un de l'autre.

# Exemples

```jldoctest
julia> A = [3. 4.; 5. 6]
2×2 Matrix{Float64}:
 3.0  4.0
 5.0  6.0

julia> B = [1. 1.; 1. 2.]
2×2 Matrix{Float64}:
 1.0  1.0
 1.0  2.0

julia> X = lyap(A, B)
2×2 Matrix{Float64}:
  0.5  -0.5
 -0.5   0.25

julia> A*X + X*A' ≈ -B
true
```
