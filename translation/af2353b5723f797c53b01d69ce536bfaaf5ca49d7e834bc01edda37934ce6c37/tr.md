```
maximum(f, itr; [init])
```

Herhangi bir `itr` elemanında `f` fonksiyonunu çağırarak elde edilen en büyük sonucu döndürür.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, `max` için nötr bir eleman olmalıdır (yani, diğer herhangi bir elemandan küçük veya ona eşit olmalıdır) çünkü `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmayacağı belirtilmemiştir.

!!! compat "Julia 1.6"
    Anahtar kelime argümanı `init`, Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> maximum(length, ["Julion", "Julia", "Jule"])
6

julia> maximum(length, []; init=-1)
-1

julia> maximum(sin, Real[]; init=-1.0)  # iyi, çünkü sin'in çıktısı >= -1
-1.0
```
