```
gcd(x, y...)
```

最大公约数（正数）（如果所有参数为零，则为零）。参数可以是整数和有理数。

!!! compat "Julia 1.4"
    有理数参数需要 Julia 1.4 或更高版本。


# 示例

```jldoctest
julia> gcd(6, 9)
3

julia> gcd(6, -9)
3

julia> gcd(6, 0)
6

julia> gcd(0, 0)
0

julia> gcd(1//3, 2//3)
1//3

julia> gcd(1//3, -2//3)
1//3

julia> gcd(1//3, 2)
1//3

julia> gcd(0, 0, 10, 15)
5
```
