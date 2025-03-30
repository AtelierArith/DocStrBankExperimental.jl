```
divrem(x, y, r::RoundingMode=RoundToZero)
```

Euclidean bölme işlemi ile elde edilen bölüm ve kalanı döndürür. `(div(x, y, r), rem(x, y, r))` ile eşdeğerdir. Eşit olarak, `r`'nin varsayılan değeri ile bu çağrı `(x ÷ y, x % y)` ile eşdeğerdir.

Ayrıca bakınız: [`fldmod`](@ref), [`cld`](@ref).

# Örnekler

```jldoctest
julia> divrem(3, 7)
(0, 3)

julia> divrem(7, 3)
(2, 1)
```
