```
findmin(f, domain) -> (f(x), index)
```

코도메인에서 값의 쌍(즉, `f`의 출력)과 해당 값의 인덱스 또는 키를 반환합니다. 이 값은 `domain`(즉, `f`의 입력)에서 `f(x)`가 최소화되는 지점입니다. 최소 지점이 여러 개일 경우, 첫 번째 지점이 반환됩니다.

`domain`은 비어 있지 않은 반복 가능 객체여야 합니다.

인덱스는 [`keys(domain)`](@ref) 및 [`pairs(domain)`](@ref)에서 반환되는 것과 동일한 유형입니다.

`NaN`은 `missing`을 제외한 모든 다른 값보다 작게 처리됩니다.

!!! compat "Julia 1.7"
    이 메서드는 Julia 1.7 이상이 필요합니다.


# 예제

```jldoctest
julia> findmin(identity, 5:9)
(5, 1)

julia> findmin(-, 1:10)
(-10, 10)

julia> findmin(first, [(2, :a), (2, :b), (3, :c)])
(2, 1)

julia> findmin(cos, 0:π/2:2π)
(-1.0, 3)
```
