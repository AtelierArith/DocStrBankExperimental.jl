```
setproperty!(value, name::Symbol, x)
setproperty!(value, name::Symbol, x, order::Symbol)
```

语法 `a.b = c` 调用 `setproperty!(a, :b, c)`。语法 `@atomic order a.b = c` 调用 `setproperty!(a, :b, c, :order)`，而语法 `@atomic a.b = c` 调用 `setproperty!(a, :b, c, :sequentially_consistent)`。

!!! compat "Julia 1.8"
    在模块上使用 `setproperty!` 至少需要 Julia 1.8。


另请参见 [`setfield!`](@ref Core.setfield!), [`propertynames`](@ref Base.propertynames) 和 [`getproperty`](@ref Base.getproperty)。
