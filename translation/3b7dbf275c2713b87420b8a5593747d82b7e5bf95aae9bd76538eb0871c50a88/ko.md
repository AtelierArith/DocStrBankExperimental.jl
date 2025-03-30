```
findmax(f, domain) -> (f(x), index)
```

코도메인에서 값의 쌍(즉, `f`의 출력)과 해당 값의 `domain`에서의 인덱스 또는 키(즉, `f`의 입력)를 반환하여 `f(x)`가 최대화되도록 합니다. 최대점이 여러 개일 경우, 첫 번째 점이 반환됩니다.

`domain`은 [`keys`](@ref)를 지원하는 비어 있지 않은 반복 가능 객체여야 합니다. 인덱스는 [`keys(domain)`](@ref)에서 반환된 것과 동일한 유형입니다.

값은 `isless`로 비교됩니다.

!!! compat "Julia 1.7"
    이 메서드는 Julia 1.7 이상이 필요합니다.


# 예제

```jldoctest
julia> findmax(identity, 5:9)
(9, 5)

julia> findmax(-, 1:10)
(-1, 1)

julia> findmax(first, [(1, :a), (3, :b), (3, :c)])
(3, 2)

julia> findmax(cos, 0:π/2:2π)
(1.0, 1)
```
