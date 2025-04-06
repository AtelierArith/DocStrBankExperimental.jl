```
unsafe_store!(p::Ptr{T}, x, i::Integer=1)
unsafe_store!(p::Ptr{T}, x, order::Symbol)
unsafe_store!(p::Ptr{T}, x, i::Integer, order::Symbol)
```

`T` türünde bir değeri `p` adresinden başlayarak `i`'nci elemanın (1'den başlayan) adresine kaydeder. Bu, C ifadesi `p[i-1] = x` ile eşdeğerdir. İsteğe bağlı olarak, atomik bellek sıralaması sağlanabilir.

Bu işlevdeki `unsafe` ön eki, `p` işaretçisinin geçerli olduğunu doğrulamak için herhangi bir doğrulama yapılmadığını gösterir. C'de olduğu gibi, programcı, bu işlev çağrılırken referans verilen belleğin serbest bırakılmadığından veya çöp toplayıcı tarafından toplanmadığından emin olmaktan sorumludur. Yanlış kullanım programınızı segfault yapabilir. C'den farklı olarak, farklı türde tahsis edilmiş bellek bölgesine veri kaydetmek, türlerin uyumlu olması koşuluyla geçerli olabilir.

!!! compat "Julia 1.10"
    `order` argümanı Julia 1.10 itibarıyla mevcuttur.


Ayrıca bakınız: [`atomic`](@ref)
