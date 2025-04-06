```
nextprod(factors::Union{Tuple,AbstractVector}, n)
```

`n`'ye eşit veya daha büyük olan ve `factors` içindeki faktörler için $k_i^{p_i}$ şeklinde yazılabilen en küçük tam sayı.

# Örnekler

```jldoctest
julia> nextprod((2, 3), 105)
108

julia> 2^2 * 3^3
108
```

!!! compat "Julia 1.6"
    Bir tuple kabul eden yöntem, Julia 1.6 veya daha yenisini gerektirir.

