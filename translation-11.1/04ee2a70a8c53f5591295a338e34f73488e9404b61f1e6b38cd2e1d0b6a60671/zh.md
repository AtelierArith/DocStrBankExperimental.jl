```
Core.memoryref_isassigned(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

返回 `MemoryRef` 中是否存储了值，如果 `Memory` 为空则返回 false。请参见 [`isassigned(::Base.RefValue)`](@ref)，[`Core.memoryrefget`](@ref)。指定的内存顺序必须与 `isatomic` 参数兼容。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。

