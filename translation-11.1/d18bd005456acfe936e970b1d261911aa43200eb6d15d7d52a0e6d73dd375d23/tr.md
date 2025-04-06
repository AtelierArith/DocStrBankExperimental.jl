```
maximum(itr; [init])
```

Bir koleksiyondaki en büyük öğeyi döndürür.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, `max` için nötr bir eleman olmalıdır (yani, diğer herhangi bir elemandan küçük veya ona eşit olmalıdır) çünkü `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmayacağı belirtilmemiştir.

!!! compat "Julia 1.6"
    Anahtar argümanı `init`, Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> maximum(-20.5:10)
9.5

julia> maximum([1,2,3])
3

julia> maximum(())
HATA: ArgumentError: boş bir koleksiyon üzerinde azaltma yapmak izin verilmez; azaltıcıya `init` sağlamayı düşünün
Yığın izi:
[...]

julia> maximum((); init=-Inf)
-Inf
```
