```
replace(A, old_new::Pair...; [count::Integer])
```

컬렉션 `A`의 복사본을 반환하며, `old_new`의 각 쌍 `old=>new`에 대해 `old`의 모든 발생이 `new`로 대체됩니다. 동등성은 [`isequal`](@ref)을 사용하여 결정됩니다. `count`가 지정된 경우, 총 `count` 발생까지만 대체됩니다.

결과의 요소 유형은 `A`의 요소 유형과 쌍의 `new` 값의 유형을 기반으로 하여 승격(promote)을 사용하여 선택됩니다(자세한 내용은 [`promote_type`](@ref) 참조). `count`가 생략되고 `A`의 요소 유형이 `Union`인 경우, 다른 유형의 값으로 대체되는 단일 유형은 결과의 요소 유형에 포함되지 않습니다: 예를 들어, `Union{T,Missing}`는 `missing`이 대체되면 `T`가 됩니다.

또한 [`replace!`](@ref), [`splice!`](@ref), [`delete!`](@ref), [`insert!`](@ref)도 참조하십시오.

!!! compat "Julia 1.7"
    `Tuple`의 요소를 대체하려면 버전 1.7이 필요합니다.


# 예제

```jldoctest
julia> replace([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace([1, missing], missing=>0)
2-element Vector{Int64}:
 1
 0
```
