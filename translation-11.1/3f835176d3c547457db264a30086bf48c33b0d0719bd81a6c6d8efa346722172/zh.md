```
prod(f, itr; [init])
```

返回将 `f` 应用于 `itr` 中每个元素的乘积。

返回类型对于小于系统字大小的有符号整数为 `Int`，对于小于系统字大小的无符号整数为 `UInt`。对于所有其他参数，找到一个共同的返回类型，以便所有参数都被提升到该类型。

对于空的 `itr`，返回的值可以通过 `init` 指定。它必须是乘法单位（即一），因为未指定 `init` 是否用于非空集合。

!!! compat "Julia 1.6"
    关键字参数 `init` 需要 Julia 1.6 或更高版本。


# 示例

```jldoctest
julia> prod(abs2, [2; 3; 4])
576
```
