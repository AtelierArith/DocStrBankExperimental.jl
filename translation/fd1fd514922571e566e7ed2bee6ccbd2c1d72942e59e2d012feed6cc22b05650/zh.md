```
typemax(T)
```

给定的（实）数值 `DataType` 可表示的最高值。

另请参见：[`floatmax`](@ref), [`typemin`](@ref), [`eps`](@ref)。

# 示例

```jldoctest
julia> typemax(Int8)
127

julia> typemax(UInt32)
0xffffffff

julia> typemax(Float64)
Inf

julia> typemax(Float32)
Inf32

julia> floatmax(Float32)  # 最大的有限 Float32 浮点数
3.4028235f38
```
