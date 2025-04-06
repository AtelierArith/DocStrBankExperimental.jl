```
lq(A) -> S::LQ
```

Calculez la décomposition LQ de `A`. Le composant triangulaire inférieur de la décomposition peut être obtenu à partir de l'objet [`LQ`](@ref) `S` via `S.L`, et le composant orthogonal/unitaire via `S.Q`, de sorte que `A ≈ S.L*S.Q`.

L'itération de la décomposition produit les composants `S.L` et `S.Q`.

La décomposition LQ est la décomposition QR de `transpose(A)`, et elle est utile pour calculer la solution à norme minimale `lq(A) \ b` à un système d'équations sous-déterminé (`A` a plus de colonnes que de lignes, mais a un rang de ligne complet).

# Exemples

```jldoctest
julia> A = [5. 7.; -2. -4.]
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> S = lq(A)
LQ{Float64, Matrix{Float64}, Vector{Float64}}
L facteur :
2×2 Matrix{Float64}:
 -8.60233   0.0
  4.41741  -0.697486
Q facteur : 2×2 LinearAlgebra.LQPackedQ{Float64, Matrix{Float64}, Vector{Float64}}

julia> S.L * S.Q
2×2 Matrix{Float64}:
  5.0   7.0
 -2.0  -4.0

julia> l, q = S; # déstructuration via itération

julia> l == S.L &&  q == S.Q
true
```
