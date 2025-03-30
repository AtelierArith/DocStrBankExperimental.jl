```
unsafe_trunc(T, x)
```

`x`'in mutlak değeri `x`'in mutlak değerine eşit veya daha küçük olan `T` türünde en yakın tam sayı değerini döndürür. Eğer değer `T` tarafından temsil edilemiyorsa, rastgele bir değer döndürülecektir. Ayrıca bkz. [`trunc`](@ref).

# Örnekler

```jldoctest
julia> unsafe_trunc(Int, -2.2)
-2

julia> unsafe_trunc(Int, NaN)
-9223372036854775808
```
