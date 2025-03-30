```
frexp(val)
```

`x`'in $[1/2, 1)$ veya 0 büyüklüğünde olduğu ve `val`'ın $x \times 2^{exp}$'e eşit olduğu `(x,exp)` çiftini döndürür.

Ayrıca [`significand`](@ref), [`exponent`](@ref), [`ldexp`](@ref) bakınız.

# Örnekler

```jldoctest
julia> frexp(6.0)
(0.75, 3)

julia> significand(6.0), exponent(6.0)  # [1, 2) aralığı yerine
(1.5, 2)

julia> frexp(0.0), frexp(NaN), frexp(-Inf)  # üstel bir hata verecektir
((0.0, 0), (NaN, 0), (-Inf, 0))
```
