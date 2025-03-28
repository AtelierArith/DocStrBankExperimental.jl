```
eigvals(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> valeurs
```

Retourne les valeurs propres de `A`. Il est possible de calculer seulement un sous-ensemble des valeurs propres en spécifiant une [`UnitRange`](@ref) `irange` couvrant les indices des valeurs propres triées, par exemple, les 2ème à 8ème valeurs propres.

# Exemples

```jldoctest
julia> A = SymTridiagonal([1.; 2.; 1.], [2.; 3.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 1.0  2.0   ⋅
 2.0  2.0  3.0
  ⋅   3.0  1.0

julia> eigvals(A, 2:2)
1-element Vector{Float64}:
 0.9999999999999996

julia> eigvals(A)
3-element Vector{Float64}:
 -2.1400549446402604
  1.0000000000000002
  5.140054944640259
```
