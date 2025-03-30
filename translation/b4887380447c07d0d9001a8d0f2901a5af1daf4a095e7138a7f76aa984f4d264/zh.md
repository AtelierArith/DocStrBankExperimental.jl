```
sum(itr; [init])
```

返回集合中所有元素的总和。

返回类型为 `Int`，适用于小于系统字大小的有符号整数，返回类型为 `UInt`，适用于小于系统字大小的无符号整数。对于所有其他参数，找到一个共同的返回类型，以便所有参数都被提升到该类型。

对于空的 `itr`，返回的值可以通过 `init` 指定。它必须是加法单位（即零），因为未指定 `init` 是否用于非空集合。

!!! compat "Julia 1.6"
    关键字参数 `init` 需要 Julia 1.6 或更高版本。


另请参见: [`reduce`](@ref), [`mapreduce`](@ref), [`count`](@ref), [`union`](@ref).

# 示例

```jldoctest
julia> sum(1:20)
210

julia> sum(1:20; init = 0.0)
210.0
```
