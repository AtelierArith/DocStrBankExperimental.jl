```
replaceproperty!(x, f::Symbol, expected, desired, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

对 `x.f` 执行比较并交换操作，将其从 `expected` 更改为 `desired`，按照平等原则。可以使用语法 `@atomicreplace x.f expected => desired` 来代替函数调用形式。

另请参见 [`replacefield!`](@ref Core.replacefield!) [`setproperty!`](@ref Base.setproperty!), [`setpropertyonce!`](@ref Base.setpropertyonce!)。
