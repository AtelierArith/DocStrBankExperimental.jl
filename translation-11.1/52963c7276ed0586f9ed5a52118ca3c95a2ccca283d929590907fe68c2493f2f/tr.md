```
methods(f, [types], [module])
```

`f` için yöntem tablosunu döndür.

Eğer `types` belirtilmişse, türleri eşleşen yöntemlerin bir dizisini döndür. Eğer `module` belirtilmişse, o modülde tanımlanan yöntemlerin bir dizisini döndür. Bir dizi olarak birden fazla modül de belirtilebilir.

!!! compat "Julia 1.4"
    Bir modül belirtmek için en az Julia 1.4 gereklidir.


Ayrıca bakınız: [`which`](@ref), [`@which`](@ref Main.InteractiveUtils.@which) ve [`methodswith`](@ref Main.InteractiveUtils.methodswith).
