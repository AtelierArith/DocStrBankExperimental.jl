```
modifyglobal!(module::Module, name::Symbol, op, x, [order::Symbol=:monotonic]) -> Pair
```

Atomik olarak `op` fonksiyonunu uyguladıktan sonra bir globali almak ve ayarlamak için işlemleri gerçekleştirin.

!!! compat "Julia 1.11"
    Bu fonksiyon Julia 1.11 veya daha yenisini gerektirir.


Ayrıca [`modifyproperty!`](@ref Base.modifyproperty!) ve [`setglobal!`](@ref) ile de bakabilirsiniz.
