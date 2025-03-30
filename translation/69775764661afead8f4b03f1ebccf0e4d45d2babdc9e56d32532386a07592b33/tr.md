```
minimum(f, itr; [init])
```

Herhangi bir `itr` elemanında `f` fonksiyonunu çağırarak elde edilen en küçük sonucu döndürür.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, `min` için nötr bir eleman olmalıdır (yani, diğer herhangi bir elemandan büyük veya ona eşit olmalıdır) çünkü `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmayacağı belirtilmemiştir.

!!! compat "Julia 1.6"
    Anahtar kelime argümanı `init`, Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> minimum(length, ["Julion", "Julia", "Jule"])
4

julia> minimum(length, []; init=typemax(Int64))
9223372036854775807

julia> minimum(sin, Real[]; init=1.0)  # iyi, çünkü sin'in çıktısı <= 1
1.0
```
