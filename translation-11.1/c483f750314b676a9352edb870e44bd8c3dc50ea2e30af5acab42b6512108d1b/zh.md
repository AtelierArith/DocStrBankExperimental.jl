```
typemin(T)
```

给定的（实数）数值数据类型 `T` 可表示的最小值。

另请参见：[`floatmin`](@ref), [`typemax`](@ref), [`eps`](@ref)。

# 示例

```jldoctest
julia> typemin(Int8)
-128

julia> typemin(UInt32)
0x00000000

julia> typemin(Float16)
-Inf16

julia> typemin(Float32)
-Inf32

julia> nextfloat(-Inf32)  # 最小的有限 Float32 浮点数
-3.4028235f38
```
