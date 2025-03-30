```
ScopedValue(x)
```

创建一个在动态作用域中传播值的容器。使用 [`with`](@ref) 创建并进入一个新的动态作用域。

值只能在进入新的动态作用域时设置，并且在动态作用域的执行过程中所引用的值将保持不变。

动态作用域在任务之间传播。

# 示例

```jldoctest
julia> using Base.ScopedValues;

julia> const sval = ScopedValue(1);

julia> sval[]
1

julia> with(sval => 2) do
           sval[]
       end
2

julia> sval[]
1
```

!!! compat "Julia 1.11"
    Scoped values 在 Julia 1.11 中引入。在 Julia 1.8+ 中，可以从包 ScopedValues.jl 获得兼容的实现。

