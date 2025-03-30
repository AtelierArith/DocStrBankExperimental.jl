```
BigFloat(x::Union{Real, AbstractString} [, rounding::RoundingMode=rounding(BigFloat)]; [precision::Integer=precision(BigFloat)])
```

从 `x` 创建一个任意精度的浮点数，精度为 `precision`。`rounding` 参数指定如果转换不能精确完成，结果应朝哪个方向舍入。如果未提供，这些值将由当前全局值设置。

`BigFloat(x::Real)` 与 `convert(BigFloat,x)` 相同，除非 `x` 本身已经是 `BigFloat`，在这种情况下，它将返回一个精度设置为当前全局精度的值；`convert` 将始终返回 `x`。

`BigFloat(x::AbstractString)` 与 [`parse`](@ref) 相同。提供此功能是为了方便，因为在解析时十进制字面量会被转换为 `Float64`，因此 `BigFloat(2.1)` 可能不会产生您预期的结果。

另请参见：

  * [`@big_str`](@ref)
  * [`rounding`](@ref) 和 [`setrounding`](@ref)
  * [`precision`](@ref) 和 [`setprecision`](@ref)

!!! compat "Julia 1.1"
    `precision` 作为关键字参数需要至少 Julia 1.1。在 Julia 1.0 中，`precision` 是第二个位置参数 (`BigFloat(x, precision)`).


# 示例

```jldoctest
julia> BigFloat(2.1) # 这里的 2.1 是 Float64
2.100000000000000088817841970012523233890533447265625

julia> BigFloat("2.1") # 最接近 2.1 的 BigFloat
2.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> BigFloat("2.1", RoundUp)
2.100000000000000000000000000000000000000000000000000000000000000000000000000021

julia> BigFloat("2.1", RoundUp, precision=128)
2.100000000000000000000000000000000000007
```
