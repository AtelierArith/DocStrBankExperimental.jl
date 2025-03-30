```
mod1(x, y)
```

取整除法后的模，返回一个值 `r`，使得在正 `y` 的范围 $(0, y]$ 内 `mod(r, y) == mod(x, y)`，在负 `y` 的范围 $[y,0)$ 内也是如此。

对于整数参数和正 `y`，这等于 `mod(x, 1:y)`，因此对于基于1的索引是自然的。相比之下，`mod(x, y) == mod(x, 0:y-1)` 对于带有偏移或步幅的计算是自然的。

另见 [`mod`](@ref), [`fld1`](@ref), [`fldmod1`](@ref).

# 示例

```jldoctest
julia> mod1(4, 2)
2

julia> mod1.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  3  1  2  3  1  2  3  1  2

julia> mod1.([-0.1, 0, 0.1, 1, 2, 2.9, 3, 3.1]', 3)
1×8 Matrix{Float64}:
 2.9  3.0  0.1  1.0  2.0  2.9  3.0  0.1
```
