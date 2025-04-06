```
Core.memoryrefreplace!(::GenericMemoryRef, expected, desired,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> (; old, success::Bool)
```

Atomik olarak bir `MemoryRef` değerini almak ve koşullu olarak ayarlamak için işlemleri gerçekleştirin.

!!! uyumluluk "Julia 1.11"
    Bu işlev, Julia 1.11 veya daha yenisini gerektirir.


Ayrıca bkz. [`replaceproperty!`](@ref Base.replaceproperty!) ve [`Core.memoryrefset!`](@ref).
