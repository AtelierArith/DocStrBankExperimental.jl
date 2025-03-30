```
Core.memoryrefget(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

`MemoryRef` içinde saklanan değeri döndürür, eğer `Memory` boşsa bir `BoundsError` fırlatır. bkz. `ref[]`. Belirtilen bellek sıralaması `isatomic` parametresi ile uyumlu olmalıdır.

!!! compat "Julia 1.11"
    Bu fonksiyon Julia 1.11 veya daha yenisini gerektirir.

