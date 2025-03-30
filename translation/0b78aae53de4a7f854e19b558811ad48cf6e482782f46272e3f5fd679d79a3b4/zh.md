```
Float32(x [, mode::RoundingMode])
```

从 `x` 创建一个 `Float32`。如果 `x` 不能被精确表示，则 `mode` 决定 `x` 的舍入方式。

# 示例

```jldoctest
julia> Float32(1/3, RoundDown)
0.3333333f0

julia> Float32(1/3, RoundUp)
0.33333334f0
```

有关可用舍入模式，请参见 [`RoundingMode`](@ref)。
