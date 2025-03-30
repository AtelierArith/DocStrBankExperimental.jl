```
gcd(x, y...)
```

최대 공약수 (양수) (또는 모든 인수가 0인 경우 0). 인수는 정수 및 유리수일 수 있습니다.

!!! compat "Julia 1.4"
    유리수 인수는 Julia 1.4 이상이 필요합니다.


# 예제

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
