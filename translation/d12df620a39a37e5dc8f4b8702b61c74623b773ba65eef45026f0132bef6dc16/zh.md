```
Core.memoryrefget(::GenericMemoryRef, ordering::Symbol, boundscheck::Bool)
```

返回存储在 `MemoryRef` 中的值，如果 `Memory` 为空则抛出 `BoundsError`。参见 `ref[]`。指定的内存顺序必须与 `isatomic` 参数兼容。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。

