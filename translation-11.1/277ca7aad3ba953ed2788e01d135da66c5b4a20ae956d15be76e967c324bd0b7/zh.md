```
float(x)
```

将数字或数组转换为浮点数据类型。

另见：[`complex`](@ref), [`oftype`](@ref), [`convert`](@ref)。

# 示例

```jldoctest
julia> float(1:1000)
1.0:1.0:1000.0

julia> float(typemax(Int32))
2.147483647e9
```
