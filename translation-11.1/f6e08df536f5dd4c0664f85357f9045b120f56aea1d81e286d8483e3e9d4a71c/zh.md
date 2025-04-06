```
>>>(x, n)
```

无符号右位移运算符，`x >>> n`。对于 `n >= 0`，结果是 `x` 向右移动 `n` 位，填充 `0`。对于 `n < 0`，这等价于 `x << -n`。

对于 [`Unsigned`](@ref) 整数类型，这等价于 [`>>`](@ref)。对于 [`Signed`](@ref) 整数类型，这等价于 `signed(unsigned(x) >> n)`。

# 示例

```jldoctest
julia> Int8(-14) >>> 2
60

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(60))
"00111100"
```

[`BigInt`](@ref) 被视为具有无限大小，因此不需要填充，这等价于 [`>>`](@ref)。

另见 [`>>`](@ref)，[`<<`](@ref)。
