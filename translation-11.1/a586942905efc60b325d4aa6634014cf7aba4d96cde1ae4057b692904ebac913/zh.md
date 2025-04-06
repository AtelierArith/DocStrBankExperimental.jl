```
div(x, y)
÷(x, y)
```

来自欧几里得（整数）除法的商。通常等同于数学运算 x/y，而没有小数部分。

另请参见: [`cld`](@ref), [`fld`](@ref), [`rem`](@ref), [`divrem`](@ref).

# 示例

```jldoctest
julia> 9 ÷ 4
2

julia> -5 ÷ 3
-1

julia> 5.0 ÷ 2
2.0

julia> div.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -1  -1  -1  0  0  0  0  0  1  1  1
```
