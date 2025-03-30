```
checkindex(Bool, inds::AbstractUnitRange, index)
```

주어진 `index`가 `inds`의 경계 내에 있으면 `true`를 반환합니다. 모든 배열의 인덱스로 동작하고자 하는 사용자 정의 유형은 이 메서드를 확장하여 특화된 경계 검사 구현을 제공할 수 있습니다.

또한 [`checkbounds`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> checkindex(Bool, 1:20, 8)
true

julia> checkindex(Bool, 1:20, 21)
false
```
