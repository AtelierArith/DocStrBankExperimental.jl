```
Core.memoryrefmodify!(::GenericMemoryRef, op, value, ordering::Symbol, boundscheck::Bool) -> Pair
```

原子地执行操作以获取和设置 `MemoryRef` 值，应用函数 `op` 后。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。


另请参见 [`modifyproperty!`](@ref Base.modifyproperty!) 和 [`Core.memoryrefset!`](@ref).
