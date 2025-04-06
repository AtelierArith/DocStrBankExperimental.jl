```
modifyglobal!(module::Module, name::Symbol, op, x, [order::Symbol=:monotonic]) -> Pair
```

原子地执行操作以获取和设置全局变量，应用函数 `op`。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。


另请参见 [`modifyproperty!`](@ref Base.modifyproperty!) 和 [`setglobal!`](@ref)。
