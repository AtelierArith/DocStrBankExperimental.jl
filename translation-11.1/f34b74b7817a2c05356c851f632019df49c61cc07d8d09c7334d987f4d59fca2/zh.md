```
modifyfield!(value, name::Symbol, op, x, [order::Symbol]) -> Pair
modifyfield!(value, i::Int, op, x, [order::Symbol]) -> Pair
```

原子性地执行操作以获取和设置字段，应用函数 `op`。

```
y = getfield(value, name)
z = op(y, x)
setfield!(value, name, z)
return y => z
```

如果硬件支持（例如，原子递增），这可能会优化为适当的硬件指令，否则将使用循环。

!!! compat "Julia 1.7"
    此函数需要 Julia 1.7 或更高版本。

