```
GeneralizedSVD <: Factorization
```

Type de factorisation matricielle de la décomposition en valeurs singulières généralisée (SVD) de deux matrices `A` et `B`, telle que `A = F.U*F.D1*F.R0*F.Q'` et `B = F.V*F.D2*F.R0*F.Q'`. C'est le type de retour de [`svd(_, _)`](@ref), la fonction de factorisation matricielle correspondante.

Pour une matrice M-par-N `A` et une matrice P-par-N `B`,

  * `U` est une matrice orthogonale M-par-M,
  * `V` est une matrice orthogonale P-par-P,
  * `Q` est une matrice orthogonale N-par-N,
  * `D1` est une matrice diagonale M-par-(K+L) avec des 1 dans les K premières entrées,
  * `D2` est une matrice P-par-(K+L) dont le bloc supérieur droit L-par-L est diagonal,
  * `R0` est une matrice (K+L)-par-N dont le bloc supérieur droit (K+L)-par-(K+L) est non singulier et triangulaire supérieur,

`K+L` est le rang numérique effectif de la matrice `[A; B]`.

L'itération de la décomposition produit les composants `U`, `V`, `Q`, `D1`, `D2`, et `R0`.

Les entrées de `F.D1` et `F.D2` sont liées, comme expliqué dans la documentation LAPACK pour le [SVD généralisé](https://www.netlib.org/lapack/lug/node36.html) et la routine [xGGSVD3](https://www.netlib.org/lapack/explore-html/d6/db3/dggsvd3_8f.html) qui est appelée en dessous (dans LAPACK 3.6.0 et versions ultérieures).

# Exemples

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> F = svd(A, B)
GeneralizedSVD{Float64, Matrix{Float64}, Float64, Vector{Float64}}
U factor:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
V factor:
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0   0.0
Q factor:
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
D1 factor:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
D2 factor:
2×2 Matrix{Float64}:
 0.707107  0.0
 0.0       0.707107
R0 factor:
2×2 Matrix{Float64}:
 1.41421   0.0
 0.0      -1.41421

julia> F.U*F.D1*F.R0*F.Q'
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> F.V*F.D2*F.R0*F.Q'
2×2 Matrix{Float64}:
 -0.0  1.0
  1.0  0.0
```
