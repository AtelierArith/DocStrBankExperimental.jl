```
bunchkaufman(A, rook::Bool=false; check = true) -> S::BunchKaufman
```

Calculez la factorisation de Bunch-Kaufman [^Bunch1977] d'une matrice symétrique ou hermitienne `A` sous la forme `P'*U*D*U'*P` ou `P'*L*D*L'*P`, selon le triangle qui est stocké dans `A`, et renvoyez un objet [`BunchKaufman`](@ref). Notez que si `A` est symétrique complexe, alors `U'` et `L'` désignent les transposées non conjuguées, c'est-à-dire `transpose(U)` et `transpose(L)`.

L'itération de la décomposition produit les composants `S.D`, `S.U` ou `S.L` selon ce qui est approprié étant donné `S.uplo`, et `S.p`.

Si `rook` est `true`, un pivotement de rook est utilisé. Si `rook` est faux, le pivotement de rook n'est pas utilisé.

Lorsque `check = true`, une erreur est levée si la décomposition échoue. Lorsque `check = false`, la responsabilité de vérifier la validité de la décomposition (via [`issuccess`](@ref)) incombe à l'utilisateur.

Les fonctions suivantes sont disponibles pour les objets `BunchKaufman` : [`size`](@ref), `\`, [`inv`](@ref), [`issymmetric`](@ref), [`ishermitian`](@ref), [`getindex`](@ref).

[^Bunch1977]: J R Bunch et L Kaufman, Some stable methods for calculating inertia and solving symmetric linear systems, Mathematics of Computation 31:137 (1977), 163-179. [url](https://www.ams.org/journals/mcom/1977-31-137/S0025-5718-1977-0428694-0/).

# Exemples

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A est enveloppé en interne par Symmetric(A)
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
Facteur D :
2×2 Tridiagonal{Float64, Vector{Float64}}:
 -0.333333  0.0
  0.0       3.0
Facteur U :
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.666667
  ⋅   1.0
permutation :
2-element Vector{Int64}:
 1
 2

julia> d, u, p = S; # déstructuration via itération

julia> d == S.D && u == S.U && p == S.p
true

julia> S.U*S.D*S.U' - S.P*A*S.P'
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0

julia> S = bunchkaufman(Symmetric(A, :L))
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
Facteur D :
2×2 Tridiagonal{Float64, Vector{Float64}}:
 3.0   0.0
 0.0  -0.333333
Facteur L :
2×2 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0        ⋅
 0.666667  1.0
permutation :
2-element Vector{Int64}:
 2
 1

julia> S.L*S.D*S.L' - A[S.p, S.p]
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
