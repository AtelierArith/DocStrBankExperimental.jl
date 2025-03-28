```
LDLt <: Factorisation
```

Type de factorisation matricielle de la factorisation `LDLt` d'une matrice réelle [`SymTridiagonal`](@ref) `S` telle que `S = L*Diagonal(d)*L'`, où `L` est une matrice [`UnitLowerTriangular`](@ref) et `d` est un vecteur. L'utilisation principale d'une factorisation `LDLt` `F = ldlt(S)` est de résoudre le système d'équations linéaires `Sx = b` avec `F\b`. C'est le type de retour de [`ldlt`](@ref), la fonction de factorisation matricielle correspondante.

Les composants individuels de la factorisation `F::LDLt` peuvent être accédés via `getproperty` :

| Composant | Description                                              |
|:---------:|:-------------------------------------------------------- |
|   `F.L`   | `L` (partie triangulaire inférieure unitaire) de `LDLt`  |
|   `F.D`   | `D` (partie diagonale) de `LDLt`                         |
|  `F.Lt`   | `Lt` (partie triangulaire supérieure unitaire) de `LDLt` |
|   `F.d`   | valeurs diagonales de `D` sous forme de `Vector`         |

# Exemples

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> F = ldlt(S)
LDLt{Float64, SymTridiagonal{Float64, Vector{Float64}}}
Facteur L :
3×3 UnitLowerTriangular{Float64, SymTridiagonal{Float64, Vector{Float64}}}:
 1.0        ⋅         ⋅
 0.333333  1.0        ⋅
 0.0       0.545455  1.0
Facteur D :
3×3 Diagonal{Float64, Vector{Float64}}:
 3.0   ⋅        ⋅
  ⋅   3.66667   ⋅
  ⋅    ⋅       3.90909
```
