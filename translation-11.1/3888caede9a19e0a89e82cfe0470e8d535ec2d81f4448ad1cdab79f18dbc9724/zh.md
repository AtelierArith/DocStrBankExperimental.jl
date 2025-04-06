```
UndefInitializer
```

单例类型用于数组初始化，表示数组构造函数调用者希望得到一个未初始化的数组。另见 [`undef`](@ref)，它是 `UndefInitializer()` 的别名。

# 示例

```julia-repl
julia> Array{Float64, 1}(UndefInitializer(), 3)
3-element Array{Float64, 1}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
