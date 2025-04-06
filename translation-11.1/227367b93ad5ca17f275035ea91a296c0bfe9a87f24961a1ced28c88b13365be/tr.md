```
minimum(itr; [init])
```

Bir koleksiyondaki en küçük öğeyi döndürür.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, `min` için nötr bir eleman olmalıdır (yani, diğer herhangi bir elemandan büyük veya ona eşit olmalıdır) çünkü `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmayacağı belirsizdir.

!!! compat "Julia 1.6"
    Anahtar argümanı `init`, Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> minimum(-20.5:10)
-20.5

julia> minimum([1,2,3])
1

julia> minimum([])
HATA: ArgumentError: boş bir koleksiyon üzerinde azaltma yapmak mümkün değildir; azaltıcıya `init` sağlamayı düşünün
Stacktrace:
[...]

julia> minimum([]; init=Inf)
Inf
```
