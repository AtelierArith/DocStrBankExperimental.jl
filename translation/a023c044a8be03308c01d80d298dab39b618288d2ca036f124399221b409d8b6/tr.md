```
swapglobal!(module::Module, name::Symbol, x, [order::Symbol=:monotonic])
```

Atomik olarak, bir globali aynı anda almak ve ayarlamak için işlemleri gerçekleştirin.

!!! uyumluluk "Julia 1.11"
    Bu fonksiyon, Julia 1.11 veya daha yenisini gerektirir.


Ayrıca [`swapproperty!`](@ref Base.swapproperty!) ve [`setglobal!`](@ref) ile de bakabilirsiniz.
