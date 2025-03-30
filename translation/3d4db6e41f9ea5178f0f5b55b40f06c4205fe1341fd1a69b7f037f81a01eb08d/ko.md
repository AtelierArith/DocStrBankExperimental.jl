```
count([f=identity,] itr; init=0) -> Integer
```

`f` 함수가 `true`를 반환하는 `itr`의 요소 수를 계산합니다. `f`가 생략되면 `itr`에서 `true` 요소의 수를 계산합니다(불리언 값의 컬렉션이어야 함). `init`은 선택적으로 카운팅을 시작할 값을 지정하며, 따라서 출력 유형도 결정합니다.

!!! compat "Julia 1.6"
    `init` 키워드는 Julia 1.6에서 추가되었습니다.


참고: [`any`](@ref), [`sum`](@ref).

# 예제

```jldoctest
julia> count(i->(4<=i<=6), [2,3,4,5,6])
3

julia> count([true, false, true, true])
3

julia> count(>(3), 1:7, init=0x03)
0x07
```
