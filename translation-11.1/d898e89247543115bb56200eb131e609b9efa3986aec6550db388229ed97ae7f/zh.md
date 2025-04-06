```
>>(x, n)
```

右位移运算符，`x >> n`。对于 `n >= 0`，结果是 `x` 向右移动 `n` 位，如果 `x >= 0` 则填充 `0`，如果 `x < 0` 则填充 `1`，保持 `x` 的符号。这相当于 `fld(x, 2^n)`。对于 `n < 0`，这相当于 `x << -n`。

# 示例

```jldoctest
julia> Int8(13) >> 2
3

julia> bitstring(Int8(13))
"00001101"

julia> bitstring(Int8(3))
"00000011"

julia> Int8(-14) >> 2
-4

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(-4))
"11111100"
```

另见 [`>>>`](@ref)，[`<<`](@ref)。
