```
methods(f, [types], [module])
```

返回 `f` 的方法表。

如果指定了 `types`，则返回类型匹配的方法数组。如果指定了 `module`，则返回在该模块中定义的方法数组。模块列表也可以作为数组指定。

!!! compat "Julia 1.4"
    至少需要 Julia 1.4 才能指定模块。


另请参见: [`which`](@ref), [`@which`](@ref Main.InteractiveUtils.@which) 和 [`methodswith`](@ref Main.InteractiveUtils.methodswith).
