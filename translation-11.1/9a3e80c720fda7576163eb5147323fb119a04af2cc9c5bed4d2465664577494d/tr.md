```
eps(x::AbstractFloat)
```

`x`'in *sondaki birim* (ulp) değerini döndürür. Bu, `x`'deki ardışık temsil edilebilir kayan nokta değerleri arasındaki mesafedir. Çoğu durumda, `x`'in her iki tarafındaki mesafe farklıysa, daha büyük olanı alınır, yani

```
eps(x) == max(x-prevfloat(x), nextfloat(x)-x)
```

Bu kuralın istisnaları, en küçük ve en büyük sonlu değerlerdir (örneğin, [`Float64`](@ref) için `nextfloat(-Inf)` ve `prevfloat(Inf)`), bu değerler daha küçük olanı yuvarlar.

Bu davranışın nedeni, `eps`'in kayan nokta yuvarlama hatasını sınırlamasıdır. Varsayılan `RoundNearest` yuvarlama modunda, $y$ bir reel sayı ve $x$ $y$'ye en yakın kayan nokta sayısı ise, o zaman

$$
|y-x| \leq \operatorname{eps}(x)/2.
$$

Ayrıca bakınız: [`nextfloat`](@ref), [`issubnormal`](@ref), [`floatmax`](@ref).

# Örnekler

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(prevfloat(2.0))
2.220446049250313e-16

julia> eps(2.0)
4.440892098500626e-16

julia> x = prevfloat(Inf)      # en büyük sonlu Float64
1.7976931348623157e308

julia> x + eps(x)/2            # yukarı yuvarlar
Inf

julia> x + prevfloat(eps(x)/2) # aşağı yuvarlar
1.7976931348623157e308
```
