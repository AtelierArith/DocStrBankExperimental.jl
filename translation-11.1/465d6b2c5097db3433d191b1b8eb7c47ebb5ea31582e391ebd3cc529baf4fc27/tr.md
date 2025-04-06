```
trunc([T,] x)
trunc(x; digits::Integer= [, base = 10])
trunc(x; sigdigits::Integer= [, base = 10])
```

`trunc(x)` x'in mutlak değeri `x`'in mutlak değerine eşit veya daha küçük olan aynı türdeki en yakın tam sayıyı döndürür.

`trunc(T, x)` sonucu `T` türüne dönüştürür, eğer kesilmiş değer `T` olarak temsil edilemiyorsa bir `InexactError` fırlatır.

`digits`, `sigdigits` ve `base` anahtar kelimeleri [`round`](@ref) için olduğu gibi çalışır.

Yeni bir tür için `trunc`'u desteklemek için `Base.round(x::NewType, ::RoundingMode{:ToZero})` tanımlayın.

Ayrıca bkz: [`%`](@ref rem), [`floor`](@ref), [`unsigned`](@ref), [`unsafe_trunc`](@ref).

# Örnekler

```jldoctest
julia> trunc(2.22)
2.0

julia> trunc(-2.22, digits=1)
-2.2

julia> trunc(Int, -2.22)
-2
```
