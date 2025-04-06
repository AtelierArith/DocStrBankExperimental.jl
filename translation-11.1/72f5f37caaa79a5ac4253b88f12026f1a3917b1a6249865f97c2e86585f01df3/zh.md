```
StepRange{T, S} <: OrdinalRange{T, S}
```

具有类型 `T` 的元素和类型 `S` 的间隔的范围。每个元素之间的步长是恒定的，范围是根据类型为 `T` 的 `start` 和 `stop` 以及类型为 `S` 的 `step` 定义的。`T` 和 `S` 都不应为浮点类型。语法 `a:b:c` 在 `b != 0` 且 `a`、`b` 和 `c` 都是整数的情况下会创建一个 `StepRange`。

# 示例

```jldoctest
julia> collect(StepRange(1, Int8(2), 10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9

julia> typeof(StepRange(1, Int8(2), 10))
StepRange{Int64, Int8}

julia> typeof(1:3:6)
StepRange{Int64, Int64}
```
