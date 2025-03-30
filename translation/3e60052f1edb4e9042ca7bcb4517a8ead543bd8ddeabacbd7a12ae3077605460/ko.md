```
filter!(f, a)
```

컬렉션 `a`를 업데이트하여 `f`가 `false`인 요소를 제거합니다. 함수 `f`는 하나의 인수를 받습니다.

# 예제

```jldoctest
julia> filter!(isodd, Vector(1:10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
