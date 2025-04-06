```
splice!(a::Vector, index::Integer, [replacement]) -> item
```

주어진 인덱스에서 항목을 제거하고 제거된 항목을 반환합니다. 이후 항목들은 남은 간격을 채우기 위해 왼쪽으로 이동합니다. 지정된 경우, 정렬된 컬렉션의 대체 값이 제거된 항목 대신에 삽입됩니다.

참고: [`replace`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`pop!`](@ref), [`popat!`](@ref).

# 예제

```jldoctest
julia> A = [6, 5, 4, 3, 2, 1]; splice!(A, 5)
2

julia> A
5-element Vector{Int64}:
 6
 5
 4
 3
 1

julia> splice!(A, 5, -1)
1

julia> A
5-element Vector{Int64}:
  6
  5
  4
  3
 -1

julia> splice!(A, 1, [-1, -2, -3])
6

julia> A
7-element Vector{Int64}:
 -1
 -2
 -3
  5
  4
  3
 -1
```

항목을 제거하지 않고 인덱스 `n` 앞에 `replacement`를 삽입하려면 `splice!(collection, n:n-1, replacement)`를 사용하세요.
