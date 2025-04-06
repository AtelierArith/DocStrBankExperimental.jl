```
abs(x)
```

`x`'in mutlak değeri.

`abs` işlevi işaretli tam sayılara uygulandığında, taşma meydana gelebilir ve bu da negatif bir değerin döndürülmesine neden olabilir. Bu taşma, yalnızca `abs` işlevi işaretli bir tam sayının temsil edilebilen en küçük değerine uygulandığında gerçekleşir. Yani, `x == typemin(typeof(x))` olduğunda, `abs(x) == x < 0` olur, beklenildiği gibi `-x` değil.

Ayrıca bakınız: [`abs2`](@ref), [`unsigned`](@ref), [`sign`](@ref).

# Örnekler

```jldoctest
julia> abs(-3)
3

julia> abs(1 + im)
1.4142135623730951

julia> abs.(Int8[-128 -127 -126 0 126 127])  # typemin(Int8) üzerinde taşma
1×6 Matrix{Int8}:
 -128  127  126  0  126  127

julia> maximum(abs, [1, -2, 3, -4])
4
```
