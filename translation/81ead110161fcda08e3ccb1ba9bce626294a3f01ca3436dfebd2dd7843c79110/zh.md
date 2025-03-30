```
Core.memoryrefswap!(::GenericMemoryRef, value, ordering::Symbol, boundscheck::Bool)
```

原子性地执行操作，同时获取和设置 `MemoryRef` 值。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。


另请参见 [`swapproperty!`](@ref Base.swapproperty!) 和 [`Core.memoryrefset!`](@ref).
