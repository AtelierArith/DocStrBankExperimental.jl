```
isassigned(array, i) -> Bool
```

주어진 배열이 인덱스 `i`와 연관된 값을 가지고 있는지 테스트합니다. 인덱스가 범위를 벗어나거나 정의되지 않은 참조가 있는 경우 `false`를 반환합니다.

# 예제

```jldoctest
julia> isassigned(rand(3, 3), 5)
true

julia> isassigned(rand(3, 3), 3 * 3 + 1)
false

julia> mutable struct Foo end

julia> v = similar(rand(3), Foo)
3-element Vector{Foo}:
 #undef
 #undef
 #undef

julia> isassigned(v, 1)
false
```
