```
setpropertyonce!(x, f::Symbol, value, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

对 `x.f` 执行比较并交换操作，如果之前未设置，则将其设置为 `value`。可以使用语法 `@atomiconce x.f = value` 来代替函数调用形式。

另请参见 [`setfieldonce!`](@ref Core.replacefield!), [`setproperty!`](@ref Base.setproperty!), [`replaceproperty!`](@ref Base.replaceproperty!).

!!! compat "Julia 1.11"
    此函数需要 Julia 1.11 或更高版本。

