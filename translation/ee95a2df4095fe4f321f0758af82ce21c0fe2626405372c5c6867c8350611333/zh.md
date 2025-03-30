```
ndigits(n::Integer; base::Integer=10, pad::Integer=1)
```

计算以 `base` 进制表示的整数 `n` 的位数（`base` 不能为 `[-1, 0, 1]`），可选地用零填充到指定大小（结果永远不会小于 `pad`）。

另见 [`digits`](@ref), [`count_ones`](@ref).

# 示例

```jldoctest
julia> ndigits(0)
1

julia> ndigits(12345)
5

julia> ndigits(1022, base=16)
3

julia> string(1022, base=16)
"3fe"

julia> ndigits(123, pad=5)
5

julia> ndigits(-123)
3
```
