```
LQ <: Factorization
```

Type de factorisation matricielle de la factorisation `LQ` d'une matrice `A`. La décomposition `LQ` est la décomposition [`QR`](@ref) de `transpose(A)`. C'est le type de retour de [`lq`](@ref), la fonction de factorisation matricielle correspondante.

Si `S::LQ` est l'objet de factorisation, le composant triangulaire inférieur peut être obtenu via `S.L`, et le composant orthogonal/unitaire via `S.Q`, tel que `A ≈ S.L*S.Q`.

L'itération de la décomposition produit les composants `S.L` et `S.Q`.

# Exemples

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matrix{Float64}, Vector{Float64}}
L facteur:
2×2 Matrix{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Q facteur: 2×2 LinearAlgebra.LQPackedQ{Float64, Matrix{Float64}, Vector{Float64}}

julia> S.L * S.Q
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # déstructuration via itération

julia> l == S.L &&  q == S.Q
true
```
