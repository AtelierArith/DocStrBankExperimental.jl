```
undef
```

`UndefInitializer()` 的别名，它构造了单例类型 [`UndefInitializer`](@ref) 的实例，用于数组初始化，以指示数组构造调用者希望得到一个未初始化的数组。

另请参见：[`missing`](@ref)，[`similar`](@ref)。

# 示例

```julia-repl
julia> Array{Float64, 1}(undef, 3)
3-element Vector{Float64}:
 2.2752528595e-314
 2.202942107e-314
 2.275252907e-314
```
