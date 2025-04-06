```
eigvecs(A, B) -> Matrix
```

Retourne une matrice `M` dont les colonnes sont les vecteurs propres généralisés de `A` et `B`. (Le `k`-ème vecteur propre peut être obtenu à partir de la tranche `M[:, k]`.)

# Exemples

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> eigvecs(A, B)
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im
```
