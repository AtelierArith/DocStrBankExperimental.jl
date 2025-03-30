```
exp2(x)
```

`x`'in taban 2 üstelini hesaplar, diğer bir deyişle $2^x$.

Ayrıca bkz. [`ldexp`](@ref), [`<<`](@ref).

# Örnekler

```jldoctest
julia> exp2(5)
32.0

julia> 2^5
32

julia> exp2(63) > typemax(Int)
true
```
