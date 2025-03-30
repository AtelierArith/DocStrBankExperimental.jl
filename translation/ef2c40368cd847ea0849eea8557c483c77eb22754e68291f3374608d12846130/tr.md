```
nextpow(a, x)
```

`x`'ten küçük olmayan en küçük `a^n`, burada `n` pozitif bir tam sayıdır. `a` 1'den büyük olmalı ve `x` 0'dan büyük olmalıdır.

Ayrıca [`prevpow`](@ref) bakınız.

# Örnekler

```jldoctest
julia> nextpow(2, 7)
8

julia> nextpow(2, 9)
16

julia> nextpow(5, 20)
25

julia> nextpow(4, 16)
16
```
