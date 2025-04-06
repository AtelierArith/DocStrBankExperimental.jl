```
Float64(x [, mode::RoundingMode])
```

从 `x` 创建一个 `Float64`。如果 `x` 不能被精确表示，则 `mode` 决定 `x` 的舍入方式。

# 示例

```jldoctest
julia> Float64(pi, RoundDown)
3.141592653589793

julia> Float64(pi, RoundUp)
3.1415926535897936
```

有关可用舍入模式，请参见 [`RoundingMode`](@ref)。
