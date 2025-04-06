```
Core.memoryref_isassigned(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

`MemoryRef`'te bir değer olup olmadığını döndürür, `Memory` boşsa false döner. [`isassigned(::Base.RefValue)`](@ref), [`Core.memoryrefget`](@ref) bakınız. Belirtilen bellek sıralaması `isatomic` parametresi ile uyumlu olmalıdır.

!!! compat "Julia 1.11"
    Bu fonksiyon Julia 1.11 veya daha yenisini gerektirir.

