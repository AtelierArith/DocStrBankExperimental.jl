```
replace!(A, old_new::Pair...; [count::Integer])
```

각 쌍 `old=>new`에 대해 `old_new`에서, 컬렉션 `A`에서 `old`의 모든 발생을 `new`로 교체합니다. 동등성은 [`isequal`](@ref)을 사용하여 결정됩니다. `count`가 지정된 경우, 총 `count` 발생까지만 교체합니다. 또한 [`replace`](@ref replace(A, old_new::Pair...))를 참조하십시오.

# 예제

```jldoctest
julia> replace!([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace!(Set([1, 2, 3]), 1=>0)
Set{Int64} with 3 elements:
  0
  2
  3
```
