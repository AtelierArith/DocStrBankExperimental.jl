```
BunchKaufman <: Factorization
```

Type de factorisation matricielle de la factorisation de Bunch-Kaufman d'une matrice symétrique ou hermitienne `A` sous la forme `P'UDU'P` ou `P'LDL'P`, selon que le triangle supérieur (par défaut) ou le triangle inférieur est stocké dans `A`. Si `A` est symétrique complexe, alors `U'` et `L'` désignent les transposées non conjuguées, c'est-à-dire `transpose(U)` et `transpose(L)`, respectivement. C'est le type de retour de [`bunchkaufman`](@ref), la fonction de factorisation matricielle correspondante.

Si `S::BunchKaufman` est l'objet de factorisation, les composants peuvent être obtenus via `S.D`, `S.U` ou `S.L` selon ce qui est approprié étant donné `S.uplo`, et `S.p`.

L'itération de la décomposition produit les composants `S.D`, `S.U` ou `S.L` selon ce qui est approprié étant donné `S.uplo`, et `S.p`.

# Exemples

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A est enveloppé en interne par Symmetric(A)
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D facteur:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 -0.333333  0.0
  0.0       3.0
U facteur:
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.666667
  ⋅   1.0
permutation:
2-element Vector{Int64}:
 1
 2

julia> d, u, p = S; # déstructuration via itération

julia> d == S.D && u == S.U && p == S.p
true

julia> S = bunchkaufman(Symmetric(A, :L))
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D facteur:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 3.0   0.0
 0.0  -0.333333
L facteur:
2×2 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0        ⋅
 0.666667  1.0
permutation:
2-element Vector{Int64}:
 2
 1
```
