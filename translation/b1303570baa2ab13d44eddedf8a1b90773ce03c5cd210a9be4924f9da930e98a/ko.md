```
unique!(A::AbstractVector)
```

[`isequal`](@ref)와 [`hash`](@ref)에 의해 결정된 중복 항목을 제거한 후 수정된 `A`를 반환합니다. `unique!`는 `A`의 요소를 발생하는 순서대로 반환합니다. 반환된 데이터의 순서에 신경 쓰지 않는 경우, `(sort!(A); unique!(A))`를 호출하는 것이 훨씬 더 효율적이며, `A`의 요소가 정렬될 수 있는 한 그렇습니다.

# 예제

```jldoctest
julia> unique!([1, 1, 1])
1-element Vector{Int64}:
 1

julia> A = [7, 3, 2, 3, 7, 5];

julia> unique!(A)
4-element Vector{Int64}:
 7
 3
 2
 5

julia> B = [7, 6, 42, 6, 7, 42];

julia> sort!(B);  # unique!는 정렬된 데이터를 훨씬 더 효율적으로 처리할 수 있습니다.

julia> unique!(B)
3-element Vector{Int64}:
  6
  7
 42
```
