```
mod2pi(x)
```

`2π` ile bölme sonrası modül, $[0,2π)$ aralığında döner.

Bu fonksiyon, sayısal olarak tam `2π` ile bölme sonrası modülün bir kayan nokta temsilini hesaplar ve bu nedenle `mod(x,2π)` ile tam olarak aynı değildir; çünkü `mod(x,2π)` `x`'in kayan nokta sayısı `2π` ile bölünmesine göre modülünü hesaplar.

!!! not
    Girdi değerinin formatına bağlı olarak, `2π`'ye en yakın temsil edilebilir değer `2π`'den küçük olabilir. Örneğin, `mod2pi(2π)` ifadesi `0` döndürmeyecektir, çünkü `2*π`'nin ara değeri bir `Float64`'dir ve `2*Float64(π) < 2*big(π)`'dir. Bu davranışın daha ince ayarı için [`rem2pi`](@ref) ifadesine bakın.


# Örnekler

```jldoctest
julia> mod2pi(9*pi/4)
0.7853981633974481
```
