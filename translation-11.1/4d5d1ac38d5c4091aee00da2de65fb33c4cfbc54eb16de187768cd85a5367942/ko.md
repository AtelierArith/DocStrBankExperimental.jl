```
>(x, y)
```

보다 큰 비교 연산자. `y < x`로 대체됩니다.

# 구현

일반적으로 새로운 타입은 이 함수를 대신하여 [`<`](@ref)를 구현하고, 대체 정의 `>(x, y) = y < x`에 의존해야 합니다.

# 예제

```jldoctest
julia> 'a' > 'b'
false

julia> 7 > 3 > 1
true

julia> "abc" > "abd"
false

julia> 5 > 3
true
```
