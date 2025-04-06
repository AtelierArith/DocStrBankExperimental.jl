```
sum(itr; [init])
```

Bir koleksiyondaki tüm elemanların toplamını döndürür.

Dönüş tipi, sistem kelime boyutundan daha küçük işaretli tam sayılar için `Int`, işaretsiz tam sayılar için ise `UInt`'dir. Diğer tüm argümanlar için, tüm argümanların terfi ettirildiği ortak bir dönüş tipi bulunur.

Boş `itr` için döndürülen değer `init` ile belirtilebilir. Bu, toplama kimliği (yani sıfır) olmalıdır çünkü `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmadığı belirtilmemiştir.

!!! compat "Julia 1.6"
    Anahtar kelime argümanı `init`, Julia 1.6 veya daha yeni bir sürüm gerektirir.


Ayrıca bakınız: [`reduce`](@ref), [`mapreduce`](@ref), [`count`](@ref), [`union`](@ref).

# Örnekler

```jldoctest
julia> sum(1:20)
210

julia> sum(1:20; init = 0.0)
210.0
```
