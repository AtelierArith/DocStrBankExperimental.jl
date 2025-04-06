```
clamp(x, lo, hi)
```

`lo <= x <= hi` ise `x` döner. Eğer `x > hi` ise `hi` döner. Eğer `x < lo` ise `lo` döner. Argümanlar ortak bir türe yükseltilir.

Ayrıca bkz. [`clamp!`](@ref), [`min`](@ref), [`max`](@ref).

!!! compat "Julia 1.3"
    İlk argüman olarak `missing` kullanmak en az Julia 1.3 gerektirir.


# Örnekler

```jldoctest
julia> clamp.([pi, 1.0, big(10)], 2.0, 9.0)
3-element Vector{BigFloat}:
 3.141592653589793238462643383279502884197169399375105820974944592307816406286198
 2.0
 9.0

julia> clamp.([11, 8, 5], 10, 6)  # lo > hi olan bir örnek
3-element Vector{Int64}:
  6
  6
 10
```
