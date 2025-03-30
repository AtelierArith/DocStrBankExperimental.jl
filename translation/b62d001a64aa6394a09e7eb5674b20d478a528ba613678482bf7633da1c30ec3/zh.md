```
digits([T<:Integer], n::Integer; base::T = 10, pad::Integer = 1)
```

返回一个元素类型为 `T`（默认为 `Int`）的数组，包含 `n` 在给定进制下的数字，选项上可以用零填充到指定大小。更重要的数字位于更高的索引，因此 `n == sum(digits[k]*base^(k-1) for k in eachindex(digits))`。

另请参见 [`ndigits`](@ref)，[`digits!`](@ref)，以及对于基数 2 还可以查看 [`bitstring`](@ref)，[`count_ones`](@ref)。

# 示例

```jldoctest
julia> digits(10)
2-element Vector{Int64}:
 0
 1

julia> digits(10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits(-256, base = 10, pad = 5)
5-element Vector{Int64}:
 -6
 -5
 -2
  0
  0

julia> n = rand(-999:999);

julia> n == evalpoly(13, digits(n, base = 13))
true
```
