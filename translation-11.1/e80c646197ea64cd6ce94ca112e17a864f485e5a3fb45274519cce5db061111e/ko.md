```
lcm(x, y...)
```

최소 공배수 (양수) (또는 인수가 0인 경우 0). 인수는 정수 및 유리수일 수 있습니다.

!!! compat "Julia 1.4"
    유리수 인수는 Julia 1.4 이상이 필요합니다.


# 예제

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
