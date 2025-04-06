```
mod(x, y)
rem(x, y, RoundDown)
```

`x`'in `y`'ye göre modülasyonu veya eşdeğer olarak, `y`'ye göre tabanlı bölme sonrası `x`'in kalanı, yani `x - y*fld(x,y)` ifadesi, ara yuvarlama olmadan hesaplandığında.

Sonuç, `y` ile aynı işarete sahip olacak ve büyüklüğü `abs(y)`'den küçük olacaktır (bazı istisnalarla, aşağıdaki notu inceleyin).

!!! not
    Ondalık sayılarla kullanıldığında, tam sonuç tür tarafından temsil edilemeyebilir ve bu nedenle yuvarlama hatası meydana gelebilir. Özellikle, tam sonuç `y`'ye çok yakınsa, `y`'ye yuvarlanabilir.


Ayrıca bakınız: [`rem`](@ref), [`div`](@ref), [`fld`](@ref), [`mod1`](@ref), [`invmod`](@ref).

```jldoctest
julia> mod(8, 3)
2

julia> mod(9, 3)
0

julia> mod(8.9, 3)
2.9000000000000004

julia> mod(eps(), 3)
2.220446049250313e-16

julia> mod(-eps(), 3)
3.0

julia> mod.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  0  1  2  0  1  2  0  1  2
```
