```
oneunit(x::T)
oneunit(T::Type)
```

返回 `T(one(x))`，其中 `T` 是参数的类型，或者（如果传递了类型）是参数。这与 [`one`](@ref) 对于具有维度的量不同：`one` 是无维的（一个乘法单位），而 `oneunit` 是有维的（与 `x` 的类型相同，或类型为 `T`）。

# 示例

```jldoctest
julia> oneunit(3.7)
1.0

julia> import Dates; oneunit(Dates.Day)
1 day
```
