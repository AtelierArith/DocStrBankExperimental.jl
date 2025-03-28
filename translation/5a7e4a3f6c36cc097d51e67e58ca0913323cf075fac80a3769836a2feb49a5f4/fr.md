```
cbrt(A::AbstractMatrix{<:Real})
```

Calcule la racine cubique réelle d'une matrice réelle `A`. Si `T = cbrt(A)`, alors nous avons `T*T*T ≈ A`, voir l'exemple donné ci-dessous.

Si `A` est symétrique, c'est-à-dire de type `HermOrSym{<:Real}`, alors ([`eigen`](@ref)) est utilisé pour trouver la racine cubique. Sinon, une version spécialisée de l'algorithme de racine p-th [^S03] est utilisée, qui exploite la décomposition de Schur réelle ([`schur`](@ref)) pour calculer la racine cubique.

[^S03]: Matthew I. Smith, "A Schur Algorithm for Computing Matrix pth Roots", SIAM Journal on Matrix Analysis and Applications, vol. 24, 2003, pp. 971–989. [doi:10.1137/S0895479801392697](https://doi.org/10.1137/s0895479801392697)

# Exemples

```jldoctest
julia> A = [0.927524 -0.15857; -1.3677 -1.01172]
2×2 Matrix{Float64}:
  0.927524  -0.15857
 -1.3677    -1.01172

julia> T = cbrt(A)
2×2 Matrix{Float64}:
  0.910077  -0.151019
 -1.30257   -0.936818

julia> T*T*T ≈ A
true
```
