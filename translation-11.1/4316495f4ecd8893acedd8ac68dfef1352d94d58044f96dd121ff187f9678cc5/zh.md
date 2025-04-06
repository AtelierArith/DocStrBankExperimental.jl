```
sign(x)
```

如果 `x==0`，返回零，否则返回 $x/|x|$（即，对于实数 `x`，返回 ±1）。

另请参见 [`signbit`](@ref)，[`zero`](@ref)，[`copysign`](@ref)，[`flipsign`](@ref)。

# 示例

```jldoctest
julia> sign(-4.0)
-1.0

julia> sign(99)
1

julia> sign(-0.0)
-0.0

julia> sign(0 + im)
0.0 + 1.0im
```
