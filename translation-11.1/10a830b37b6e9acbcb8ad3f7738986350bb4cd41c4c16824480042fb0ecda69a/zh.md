```
Core.memoryrefreplace!(::GenericMemoryRef, expected, desired,
                       success_order::Symbol, fail_order::Symbol=success_order, boundscheck::Bool) -> (; old, success::Bool)
```

原子地执行获取和有条件设置 `MemoryRef` 值的操作。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。


另请参见 [`replaceproperty!`](@ref Base.replaceproperty!) 和 [`Core.memoryrefset!`](@ref)。
