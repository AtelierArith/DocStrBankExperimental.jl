```
Core.memoryrefmodify!(::GenericMemoryRef, op, value, ordering::Symbol, boundscheck::Bool) -> Pair
```

Atomik olarak `op` fonksiyonunu uyguladıktan sonra bir `MemoryRef` değerini almak ve ayarlamak için işlemleri gerçekleştirin.

!!! compat "Julia 1.11"
    Bu fonksiyon Julia 1.11 veya daha yenisini gerektirir.


Ayrıca [`modifyproperty!`](@ref Base.modifyproperty!) ve [`Core.memoryrefset!`](@ref) ile ilgili bilgiye bakın.
