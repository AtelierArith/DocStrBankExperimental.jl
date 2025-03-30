```
prod(itr; [init])
```

Bir koleksiyonun tüm elemanlarının çarpımını döndürür.

Dönüş tipi, sistem kelime boyutundan daha küçük işaretli tam sayılar için `Int`, işaretsiz tam sayılar için ise `UInt`'dir. Diğer tüm argümanlar için, tüm argümanların terfi ettirildiği ortak bir dönüş tipi bulunur.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, çarpan kimliği (yani bir) olmalıdır, çünkü `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmadığı belirtilmemiştir.

!!! compat "Julia 1.6"
    Anahtar kelime argümanı `init`, Julia 1.6 veya daha yeni bir sürüm gerektirir.


Ayrıca bakınız: [`reduce`](@ref), [`cumprod`](@ref), [`any`](@ref).

# Örnekler

```jldoctest
julia> prod(1:5)
120

julia> prod(1:5; init = 1.0)
120.0
```
