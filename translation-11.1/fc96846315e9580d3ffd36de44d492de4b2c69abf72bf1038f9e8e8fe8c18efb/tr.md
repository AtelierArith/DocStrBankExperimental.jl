```
Core.memoryrefset!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

`MemoryRef`'e değeri saklayın, `Memory` boşsa bir `BoundsError` fırlatın. `ref[] = value` şeklinde düşünün. Belirtilen bellek sıralaması `isatomic` parametresi ile uyumlu olmalıdır.

!!! compat "Julia 1.11"
    Bu fonksiyon Julia 1.11 veya daha yenisini gerektirir.

