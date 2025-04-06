```
lcm(x, y...)
```

Kleinste gemeinsame (positive) Vielfache (oder null, wenn ein Argument null ist). Die Argumente können ganze und rationale Zahlen sein.

!!! compat "Julia 1.4"
    Rationale Argumente erfordern Julia 1.4 oder höher.


# Beispiele

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
