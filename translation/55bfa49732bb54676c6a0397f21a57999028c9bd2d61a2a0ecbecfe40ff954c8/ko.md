```
splice!(a::Vector, indices, [replacement]) -> items
```

지정된 인덱스에서 항목을 제거하고, 제거된 항목을 포함하는 컬렉션을 반환합니다. 이후 항목은 남은 간격을 채우기 위해 왼쪽으로 이동합니다. 지정된 경우, 정렬된 컬렉션의 대체 값이 제거된 항목 대신 삽입됩니다. 이 경우, `indices`는 `AbstractUnitRange`여야 합니다.

인덱스 `n` 앞에 항목을 제거하지 않고 `replacement`를 삽입하려면 `splice!(collection, n:n-1, replacement)`를 사용하십시오.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 경우 동작이 예기치 않게 될 수 있습니다.

!!! 호환성 "Julia 1.5"     Julia 1.5 이전에는 `indices`가 항상 `UnitRange`여야 했습니다.

!!! 호환성 "Julia 1.8"     Julia 1.8 이전에는 대체 값을 삽입할 경우 `indices`가 `UnitRange`여야 했습니다.

# 예제

```jldoctest
julia> A = [-1, -2, -3, 5, 4, 3, -1]; splice!(A, 4:3, 2)
Int64[]

julia> A
8-element Vector{Int64}:
 -1
 -2
 -3
  2
  5
  4
  3
 -1
```
