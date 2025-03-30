```
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]])
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; digits=0, base=10)
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; sigdigits, base=10)
```

Kompleks değerli `z` için aynı türdeki en yakın tam sayıyı döndürün, belirtilen [`RoundingMode`](@ref) kullanarak bağları kırın. İlk [`RoundingMode`](@ref) gerçek bileşenleri yuvarlamak için, ikincisi ise hayali bileşenleri yuvarlamak için kullanılır.

`RoundingModeReal` ve `RoundingModeImaginary` varsayılan olarak [`RoundNearest`](@ref) değerini alır; bu, en yakın tam sayıya yuvarlar ve bağlar (0.5'lik kesirli değerler) en yakın çift tam sayıya yuvarlanır.

# Örnekler

```jldoctest
julia> round(3.14 + 4.5im)
3.0 + 4.0im

julia> round(3.14 + 4.5im, RoundUp, RoundNearestTiesUp)
4.0 + 5.0im

julia> round(3.14159 + 4.512im; digits = 1)
3.1 + 4.5im

julia> round(3.14159 + 4.512im; sigdigits = 3)
3.14 + 4.51im
```
