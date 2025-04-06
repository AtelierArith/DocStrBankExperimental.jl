```
checkbounds(Bool, A, I...)
```

지정된 인덱스 `I`가 주어진 배열 `A`의 범위 내에 있으면 `true`를 반환합니다. `AbstractArray`의 하위 유형은 사용자 정의 경계 검사 동작을 제공해야 하는 경우 이 메서드를 특수화해야 합니다. 그러나 많은 경우 `A`의 인덱스와 [`checkindex`](@ref)에 의존할 수 있습니다.

또한 [`checkindex`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> A = rand(3, 3);

julia> checkbounds(Bool, A, 2)
true

julia> checkbounds(Bool, A, 3, 4)
false

julia> checkbounds(Bool, A, 1:3)
true

julia> checkbounds(Bool, A, 1:3, 2:4)
false
```
