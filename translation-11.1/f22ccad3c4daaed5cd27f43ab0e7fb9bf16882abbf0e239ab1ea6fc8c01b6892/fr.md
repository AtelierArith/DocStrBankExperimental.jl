```
eigvecs(A; permute::Bool=true, scale::Bool=true, `sortby`) -> Matrix
```

Renvoie une matrice `M` dont les colonnes sont les vecteurs propres de `A`. (Le `k`-ème vecteur propre peut être obtenu à partir de la tranche `M[:, k]`.) Les mots-clés `permute`, `scale` et `sortby` sont les mêmes que pour [`eigen`](@ref).

# Exemples

```jldoctest
julia> eigvecs([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```
