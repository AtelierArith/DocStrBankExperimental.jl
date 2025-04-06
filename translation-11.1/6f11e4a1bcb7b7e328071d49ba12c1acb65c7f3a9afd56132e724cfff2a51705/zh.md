```
NaN, NaN64
```

一个类型为 [`Float64`](@ref) 的非数字值。

另请参见：[`isnan`](@ref), [`missing`](@ref), [`NaN32`](@ref), [`Inf`](@ref)。

# 示例

```jldoctest
julia> 0/0
NaN

julia> Inf - Inf
NaN

julia> NaN == NaN, isequal(NaN, NaN), isnan(NaN)
(false, true, true)
```

!!! 注意     始终使用 [`isnan`](@ref) 或 [`isequal`](@ref) 来检查 `NaN`。使用 `x === NaN` 可能会给出意外的结果：

````
```julia-repl
julia> reinterpret(UInt32, NaN32)
0x7fc00000

julia> NaN32p1 = reinterpret(Float32, 0x7fc00001)
NaN32

julia> NaN32p1 === NaN32, isequal(NaN32p1, NaN32), isnan(NaN32p1)
(false, true, true)
```
````
