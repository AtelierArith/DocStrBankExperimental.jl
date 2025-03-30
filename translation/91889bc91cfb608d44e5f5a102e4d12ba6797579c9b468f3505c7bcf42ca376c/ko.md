```
iseven(x::Number) -> Bool
```

`x`가 짝수 정수(즉, 2로 나누어 떨어지는 정수)인 경우 `true`를 반환하고, 그렇지 않으면 `false`를 반환합니다.

!!! compat "Julia 1.7"
    비정수(`Integer`가 아닌) 인수는 Julia 1.7 이상이 필요합니다.


# 예제

```jldoctest
julia> iseven(9)
false

julia> iseven(10)
true
```
