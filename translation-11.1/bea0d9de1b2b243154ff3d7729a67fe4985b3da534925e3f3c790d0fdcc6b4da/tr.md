```
LogRange{T}(başlangıç, durdur, uzunluk) <: AbstractVector{T}
```

`başlangıç` ve `durdur` arasında logaritmik olarak aralıklı elemanlara sahip bir aralık, aralık `uzunluk` ile kontrol edilir. [`logrange`](@ref) tarafından döndürülür.

[`LinRange`](@ref) gibi, ilk ve son elemanlar tam olarak sağlananlar olacaktır, ancak ara değerlerde küçük kayan nokta hataları olabilir. Bu değerler, inşaat sırasında saklanan uç noktaların logaritmaları kullanılarak hesaplanır ve genellikle `T`'den daha yüksek bir hassasiyetle saklanır.

# Örnekler

```jldoctest
julia> logrange(1, 4, length=5)
5-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 1.41421, 2.0, 2.82843, 4.0

julia> Base.LogRange{Float16}(1, 4, 5)
5-element Base.LogRange{Float16, Float64}:
 1.0, 1.414, 2.0, 2.828, 4.0

julia> logrange(1e-310, 1e-300, 11)[1:2:end]
6-element Vector{Float64}:
 1.0e-310
 9.999999999999974e-309
 9.999999999999981e-307
 9.999999999999988e-305
 9.999999999999994e-303
 1.0e-300

julia> prevfloat(1e-308, 5) == ans[2]
true
```

Tam sayı eltipi `T`'ye izin verilmez. Örneğin `round.(Int, xs)` veya bazı tam sayı tabanlarının açık kuvvetlerini kullanın:

```jldoctest
julia> xs = logrange(1, 512, 4)
4-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 8.0, 64.0, 512.0

julia> 2 .^ (0:3:9) |> println
[1, 8, 64, 512]
```

!!! uyumluluk "Julia 1.11"
    Bu tür en az Julia 1.11 gerektirir.

