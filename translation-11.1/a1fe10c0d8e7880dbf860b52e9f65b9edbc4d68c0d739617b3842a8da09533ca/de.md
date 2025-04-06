```
eigvals(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> values
```

Gibt die Eigenwerte von `A` zurück. Es ist möglich, nur eine Teilmenge der Eigenwerte zu berechnen, indem man einen [`UnitRange`](@ref) `irange` angibt, der Indizes der sortierten Eigenwerte abdeckt, z.B. die 2. bis 8. Eigenwerte.

# Beispiele

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
