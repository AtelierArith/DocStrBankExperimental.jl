```
setglobalonce!(module::Module, name::Symbol, value,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

原子地执行操作，将全局变量设置为给定值，仅在之前未设置的情况下。

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。


另请参见 [`setpropertyonce!`](@ref Base.setpropertyonce!) 和 [`setglobal!`](@ref).
