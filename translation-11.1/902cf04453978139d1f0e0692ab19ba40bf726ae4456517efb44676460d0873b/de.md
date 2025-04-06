```
exp2(x)
```

Berechne die Basis-2-Exponentialfunktion von `x`, mit anderen Worten $2^x$.

Siehe auch [`ldexp`](@ref), [`<<`](@ref).

# Beispiele

```jldoctest
julia> exp2(5)
32.0

julia> 2^5
32

julia> exp2(63) > typemax(Int)
true
```
