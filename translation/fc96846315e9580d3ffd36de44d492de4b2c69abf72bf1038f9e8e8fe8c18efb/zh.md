```
Core.memoryrefset!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

将值存储到 `MemoryRef`，如果 `Memory` 为空则抛出 `BoundsError`。参见 `ref[] = value`。指定的内存顺序必须与 `isatomic` 参数兼容。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。

