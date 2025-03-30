```
unsafe_load(p::Ptr{T}, i::Integer=1)
unsafe_load(p::Ptr{T}, order::Symbol)
unsafe_load(p::Ptr{T}, i::Integer, order::Symbol)
```

`p` adresindeki `i`'nci elemanın (1'den başlayan indeks) değerini `T` türünde yükler. Bu, C ifadesi `p[i-1]` ile eşdeğerdir. İsteğe bağlı olarak, atomik bellek sıralaması sağlanabilir.

Bu işlevdeki `unsafe` ön eki, `p` işaretçisinin geçerli olduğunu doğrulamak için herhangi bir doğrulama yapılmadığını belirtir. C'de olduğu gibi, programcı, bu işlev çağrılırken referans verilen belleğin serbest bırakılmadığından veya çöp toplayıcı tarafından toplanmadığından emin olmaktan sorumludur. Yanlış kullanım, programınızı segfault yapabilir veya geçersiz sonuçlar döndürebilir. C'den farklı olarak, farklı türde tahsis edilmiş bellek bölgesinin dereferans edilmesi, türlerin uyumlu olması koşuluyla geçerli olabilir.

!!! compat "Julia 1.10"
    `order` argümanı Julia 1.10'dan itibaren mevcuttur.


Ayrıca bakınız: [`atomic`](@ref)
