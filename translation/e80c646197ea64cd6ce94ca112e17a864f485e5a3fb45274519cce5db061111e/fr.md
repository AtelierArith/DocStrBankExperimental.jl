```
lcm(x, y...)
```

Plus petit multiple commun (positif) (ou zéro si un argument est zéro). Les arguments peuvent être des nombres entiers et rationnels.

!!! compat "Julia 1.4"
    Les arguments rationnels nécessitent Julia 1.4 ou une version ultérieure.


# Exemples

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
