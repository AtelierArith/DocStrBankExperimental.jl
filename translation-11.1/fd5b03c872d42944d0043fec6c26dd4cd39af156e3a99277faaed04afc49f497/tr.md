```
Float32 <: AbstractFloat <: Real
```

32-bit kayan nokta türü (IEEE 754 standardı). İkili format 1 işaret, 8 üs, 23 kesir bitidir.

Bilimsel gösterim için üs, küçük harf `f` olarak girilmelidir, bu nedenle `2f3 === 2.0f0 * 10^3 === Float32(2_000)`. Dizi literalleri ve kavramları için, eleman türü köşeli parantezlerden önce belirtilebilir: `Float32[1,4,9] == Float32[i^2 for i in 1:3]`.

Ayrıca [`Inf32`](@ref), [`NaN32`](@ref), [`Float16`](@ref), [`exponent`](@ref), [`frexp`](@ref) bakınız.
