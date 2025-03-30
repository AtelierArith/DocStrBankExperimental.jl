```
Core.memoryrefswap!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

Atomik olarak bir `MemoryRef` değerini aynı anda almak ve ayarlamak için işlemleri gerçekleştirin.

!!! compat "Julia 1.11"
    Bu fonksiyon Julia 1.11 veya daha yenisini gerektirir.


Ayrıca [`swapproperty!`](@ref Base.swapproperty!) ve [`Core.memoryrefset!`](@ref) ile de bakabilirsiniz.
