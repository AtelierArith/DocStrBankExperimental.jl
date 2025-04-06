```
bitstring(n)
```

一个字符串，给出原始类型的字面位表示。

另见 [`count_ones`](@ref), [`count_zeros`](@ref), [`digits`](@ref).

# 示例

```jldoctest
julia> bitstring(Int32(4))
"00000000000000000000000000000100"

julia> bitstring(2.2)
"0100000000000001100110011001100110011001100110011001100110011010"
```
