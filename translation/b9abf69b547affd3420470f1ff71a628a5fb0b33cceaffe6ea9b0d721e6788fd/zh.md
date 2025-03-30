```
replaceglobal!(module::Module, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

原子地执行操作以获取并有条件地将全局变量设置为给定值。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。


另请参见 [`replaceproperty!`](@ref Base.replaceproperty!) 和 [`setglobal!`](@ref).
