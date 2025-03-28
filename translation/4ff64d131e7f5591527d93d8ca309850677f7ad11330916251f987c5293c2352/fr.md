```
ldlt(S::SymTridiagonal) -> LDLt
```

Calcule une factorisation `LDLt` (c'est-à-dire, $LDL^T$) de la matrice tridiagonale symétrique réelle `S` telle que `S = L*Diagonal(d)*L'` où `L` est une matrice triangulaire inférieure unitaire et `d` est un vecteur. L'utilisation principale d'une factorisation `LDLt` `F = ldlt(S)` est de résoudre le système d'équations linéaires `Sx = b` avec `F\b`.

Voir aussi [`bunchkaufman`](@ref) pour une factorisation similaire, mais pivotée, de matrices symétriques ou hermitiennes arbitraires.

# Exemples

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> ldltS = ldlt(S);

julia> b = [6., 7., 8.];

julia> ldltS \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255

julia> S \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255
```
