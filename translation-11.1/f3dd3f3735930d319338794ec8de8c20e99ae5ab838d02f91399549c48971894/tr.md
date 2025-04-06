```
significand(x)
```

Bir kayan noktalı sayının anlamlı kısmını (diğer adıyla mantissa) çıkarır. Eğer `x` sıfırdan farklı sonlu bir sayı ise, sonuç `x` ile aynı türde ve işarete sahip bir sayı olacak ve mutlak değeri $[1,2)$ aralığında olacaktır. Aksi takdirde `x` döndürülür.

Ayrıca bkz. [`frexp`](@ref), [`exponent`](@ref).

# Örnekler

```jldoctest
julia> significand(15.2)
1.9

julia> significand(-15.2)
-1.9

julia> significand(-15.2) * 2^3
-15.2

julia> significand(-Inf), significand(Inf), significand(NaN)
(-Inf, Inf, NaN)
```
