```
sum(f, itr; [init])
```

`itr`'nin her bir elemanında `f` fonksiyonunu çağırmanın sonuçlarını toplayın.

Dönüş tipi, sistem kelime boyutundan daha küçük işaretli tam sayılar için `Int`, işaretsiz tam sayılar için ise `UInt`'dir. Tüm diğer argümanlar için, tüm argümanların terfi ettirildiği ortak bir dönüş tipi bulunur.

Boş `itr` için döndürülecek değer `init` ile belirtilebilir. Bu, toplama kimliği (yani sıfır) olmalıdır çünkü `init`'in boş olmayan koleksiyonlar için kullanılıp kullanılmadığı belirtilmemiştir.

!!! compat "Julia 1.6"
    Anahtar kelime argümanı `init`, Julia 1.6 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> sum(abs2, [2; 3; 4])
29
```

Küçük tam sayı el tipi olan diziler için `sum(A)` ve `reduce(+, A)` arasındaki önemli farkı not edin:

```jldoctest
julia> sum(Int8[100, 28])
128

julia> reduce(+, Int8[100, 28])
-128
```

İlk durumda, tam sayılar sistem kelime boyutuna genişletilir ve bu nedenle sonuç 128'dir. İkincisinde, böyle bir genişletme gerçekleşmez ve tam sayı taşması -128 sonucunu verir.
