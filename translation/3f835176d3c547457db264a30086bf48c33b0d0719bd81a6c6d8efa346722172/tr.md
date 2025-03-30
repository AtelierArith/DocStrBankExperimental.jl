```
prod(f, itr; [init])
```

`itr`'deki her bir elemana uygulanan `f`'nin çarpımını döndürür.

Dönüş tipi, sistem kelime boyutundan daha küçük işaretli tam sayılar için `Int`, işaretsiz tam sayılar için ise `UInt`'dir. Tüm diğer argümanlar için, tüm argümanların terfi ettirildiği ortak bir dönüş tipi bulunur.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, çarpan kimliği (yani bir) olmalıdır çünkü `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmadığı belirtilmemiştir.

!!! compat "Julia 1.6"
    Anahtar kelime argümanı `init`, Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> prod(abs2, [2; 3; 4])
576
```
