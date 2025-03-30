```
logrange(start, stop, length)
logrange(start, stop; length)
```

Verilen uç noktalar arasında logaritmik olarak aralıklı elemanlara sahip özel bir dizi oluşturur. Yani, ardışık elemanların oranı, uzunluktan hesaplanan sabit bir değerdir.

Bu, Python'daki `geomspace`'e benzer. Mathematica'daki `PowerRange`'in aksine, eleman sayısını belirtirsiniz, oranı değil. Python ve Matlab'daki `logspace`'in aksine, `start` ve `stop` argümanları her zaman sonucun ilk ve son elemanlarıdır, bazı birimlere uygulanmış güçler değil.

# Örnekler

```jldoctest
julia> logrange(10, 4000, length=3)
3-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 10.0, 200.0, 4000.0

julia> ans[2] ≈ sqrt(10 * 4000)  # orta eleman geometrik ortadır
true

julia> range(10, 40, length=3)[2] ≈ (10 + 40)/2  # aritmetik ortadır
true

julia> logrange(1f0, 32f0, 11)
11-element Base.LogRange{Float32, Float64}:
 1.0, 1.41421, 2.0, 2.82843, 4.0, 5.65685, 8.0, 11.3137, 16.0, 22.6274, 32.0

julia> logrange(1, 1000, length=4) ≈ 10 .^ (0:3)
true
```

Daha fazla ayrıntı için [`LogRange`](@ref Base.LogRange) türüne bakın.

Ayrıca, lineer olarak aralıklı noktalar için [`range`](@ref) ile de bakabilirsiniz.

!!! compat "Julia 1.11"
    Bu fonksiyon en az Julia 1.11 gerektirir.

