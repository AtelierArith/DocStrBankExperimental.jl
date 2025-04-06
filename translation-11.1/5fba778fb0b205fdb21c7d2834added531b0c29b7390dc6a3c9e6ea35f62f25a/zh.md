```
Bool <: Integer
```

布尔类型，包含值 `true` 和 `false`。

`Bool` 是一种数字：`false` 在数值上等于 `0`，而 `true` 在数值上等于 `1`。此外，`false` 在与 [`NaN`](@ref) 和 [`Inf`](@ref) 的乘法运算中表现为一种乘法“强零”：

```jldoctest
julia> [true, false] == [1, 0]
true

julia> 42.0 + true
43.0

julia> 0 .* (NaN, Inf, -Inf)
(NaN, NaN, NaN)

julia> false .* (NaN, Inf, -Inf)
(0.0, 0.0, -0.0)
```

通过 [`if`](@ref) 和其他条件语句的分支仅接受 `Bool`。在 Julia 中没有“真值”。

比较通常返回 `Bool`，而广播的比较可能返回 [`BitArray`](@ref) 而不是 `Array{Bool}`。

```jldoctest
julia> [1 2 3 4 5] .< pi
1×5 BitMatrix:
 1  1  1  0  0

julia> map(>(pi), [1 2 3 4 5])
1×5 Matrix{Bool}:
 0  0  0  1  1
```

另见 [`trues`](@ref)，[`falses`](@ref)，[`ifelse`](@ref)。
