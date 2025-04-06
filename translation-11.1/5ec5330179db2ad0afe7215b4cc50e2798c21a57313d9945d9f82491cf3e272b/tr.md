```
mod(x::Integer, r::AbstractUnitRange)
```

`r` aralığında `y`'yi bul, böylece $x ≡ y (mod n)$, burada `n = length(r)`, yani `y = mod(x - first(r), n) + first(r)`.

Ayrıca [`mod1`](@ref) bakın.

# Örnekler

```jldoctest
julia> mod(0, Base.OneTo(3))  # mod1(0, 3)
3

julia> mod(3, 0:2)  # mod(3, 3)
0
```

!!! uyumluluk "Julia 1.3"
    Bu yöntem en az Julia 1.3 gerektirir.

