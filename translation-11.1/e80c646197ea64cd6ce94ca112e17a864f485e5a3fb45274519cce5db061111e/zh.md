```
lcm(x, y...)
```

最小公倍数（正数）（如果任何参数为零，则为零）。参数可以是整数和有理数。

!!! compat "Julia 1.4"
    有理数参数需要 Julia 1.4 或更高版本。


# 示例

```jldoctest
julia> lcm(2, 3)
6

julia> lcm(-2, 3)
6

julia> lcm(0, 3)
0

julia> lcm(0, 0)
0

julia> lcm(1//3, 2//3)
2//3

julia> lcm(1//3, -2//3)
2//3

julia> lcm(1//3, 2)
2//1

julia> lcm(1, 3, 5, 7)
105
```
