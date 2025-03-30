```
<<(x, n)
```

左位移运算符，`x << n`。对于 `n >= 0`，结果是 `x` 向左移动 `n` 位，填充 `0`。这相当于 `x * 2^n`。对于 `n < 0`，这相当于 `x >> -n`。

# 示例

```jldoctest
julia> Int8(3) << 2
12

julia> bitstring(Int8(3))
"00000011"

julia> bitstring(Int8(12))
"00001100"
```

另请参见 [`>>`](@ref)，[`>>>`](@ref)，[`exp2`](@ref)，[`ldexp`](@ref)。
