```
retry(f;  delays=ExponentialBackOff(), check=nothing) -> Function
```

Fonksiyon `f`'yi çağıran anonim bir fonksiyon döndürür. Bir istisna oluşursa, `f` tekrar tekrar çağrılır, her seferinde `check` `true` döndüğünde, `delays`'de belirtilen saniye sayısı kadar bekledikten sonra. `check`, `delays`'in mevcut durumunu ve `Exception`'ı girmelidir.

!!! compat "Julia 1.2"
    Julia 1.2'den önce bu imza `f::Function` ile sınırlıydı.


# Örnekler

```julia
retry(f, delays=fill(5.0, 3))
retry(f, delays=rand(5:10, 2))
retry(f, delays=Base.ExponentialBackOff(n=3, first_delay=5, max_delay=1000))
retry(http_get, check=(s,e)->e.status == "503")(url)
retry(read, check=(s,e)->isa(e, IOError))(io, 128; all=false)
```
