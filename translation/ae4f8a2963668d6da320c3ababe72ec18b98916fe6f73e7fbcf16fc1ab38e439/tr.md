```
prevpow(a, x)
```

`x`'den büyük olmayan en büyük `a^n`, burada `n` sıfır veya pozitif bir tam sayıdır. `a` 1'den büyük olmalı ve `x` 1'den küçük olmamalıdır.

Ayrıca bkz. [`nextpow`](@ref), [`isqrt`](@ref).

# Örnekler

```jldoctest
julia> prevpow(2, 7)
4

julia> prevpow(2, 9)
8

julia> prevpow(5, 20)
5

julia> prevpow(4, 16)
16
```
