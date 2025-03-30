```
exponent(x::Gerçek) -> Int
```

`2^y ≤ abs(x)` koşulunu sağlayan en büyük tam sayı `y`'yi döndürür.

`x` sıfır, sonsuz veya [`NaN`](@ref) olduğunda bir `DomainError` fırlatır. Diğer herhangi bir normal olmayan kayan nokta sayısı `x` için bu, `x`'in üs bitlerine karşılık gelir.

Ayrıca [`signbit`](@ref), [`significand`](@ref), [`frexp`](@ref), [`issubnormal`](@ref), [`log2`](@ref), [`ldexp`](@ref) ile de ilgili.

# Örnekler

```jldoctest
julia> exponent(8)
3

julia> exponent(6.5)
2

julia> exponent(-1//4)
-2

julia> exponent(3.142e-4)
-12

julia> exponent(floatmin(Float32)), exponent(nextfloat(0.0f0))
(-126, -149)

julia> exponent(0.0)
HATA: DomainError ile 0.0:
±0.0 olamaz.
[...]
```
