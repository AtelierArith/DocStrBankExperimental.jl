```
<(x, y)
```

작은 비교 연산자. [`isless`](@ref)로 대체됩니다. 부동 소수점 NaN 값의 동작 때문에 이 연산자는 부분 순서를 구현합니다.

# 구현

표준 부분 순서를 가진 새로운 유형은 새로운 유형의 두 인수에 대해 이 함수를 구현해야 합니다. 표준 전체 순서를 가진 유형은 대신에 [`isless`](@ref)를 구현해야 합니다.

또한 [`isunordered`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> 'a' < 'b'
true

julia> "abc" < "abd"
true

julia> 5 < 3
false
```
