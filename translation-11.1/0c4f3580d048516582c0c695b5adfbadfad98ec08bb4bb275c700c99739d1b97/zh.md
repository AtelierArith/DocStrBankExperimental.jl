```
string(n::Integer; base::Integer = 10, pad::Integer = 1)
```

将整数 `n` 转换为给定 `base` 的字符串， 可选地指定填充到的数字位数。

另见 [`digits`](@ref), [`bitstring`](@ref), [`count_zeros`](@ref).

# 示例

```jldoctest
julia> string(5, base = 13, pad = 4)
"0005"

julia> string(-13, base = 5, pad = 4)
"-0023"
```
