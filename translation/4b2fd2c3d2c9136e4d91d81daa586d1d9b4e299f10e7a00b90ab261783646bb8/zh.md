```
swapproperty!(x, f::Symbol, v, order::Symbol=:not_atomic)
```

语法 `@atomic a.b, _ = c, a.b` 返回 `(c, swapproperty!(a, :b, c, :sequentially_consistent))`，其中两边必须有一个共同的 `getproperty` 表达式。

另请参见 [`swapfield!`](@ref Core.swapfield!) 和 [`setproperty!`](@ref Base.setproperty!)。
