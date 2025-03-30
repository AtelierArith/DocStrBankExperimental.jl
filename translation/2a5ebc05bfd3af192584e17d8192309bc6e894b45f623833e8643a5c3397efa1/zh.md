```
mod(x, y)
rem(x, y, RoundDown)
```

`x` 对 `y` 的模运算，或者等价地，`x` 在向下取整除以 `y` 后的余数，即 `x - y*fld(x,y)`，如果不进行中间舍入计算。

结果将与 `y` 具有相同的符号，且其大小小于 `abs(y)`（有一些例外，见下面的注释）。

!!! note
    当与浮点值一起使用时，确切的结果可能无法被该类型表示，因此可能会发生舍入误差。特别是，如果确切的结果非常接近 `y`，则可能会被舍入为 `y`。


另请参见: [`rem`](@ref), [`div`](@ref), [`fld`](@ref), [`mod1`](@ref), [`invmod`](@ref).

```jldoctest
julia> mod(8, 3)
2

julia> mod(9, 3)
0

julia> mod(8.9, 3)
2.9000000000000004

julia> mod(eps(), 3)
2.220446049250313e-16

julia> mod(-eps(), 3)
3.0

julia> mod.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  0  1  2  0  1  2  0  1  2
```
