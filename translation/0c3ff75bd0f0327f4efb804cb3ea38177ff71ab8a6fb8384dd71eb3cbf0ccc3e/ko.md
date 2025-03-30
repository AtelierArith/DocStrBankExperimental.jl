```
findnext(A, i)
```

`A`에서 `i` 이후 또는 `i`를 포함한 `true` 요소의 다음 인덱스를 찾거나, 없으면 `nothing`을 반환합니다.

인덱스는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환되는 것과 동일한 유형입니다.

# 예제

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findnext(A, 1)
3

julia> findnext(A, 4) # 반환은 nothing이지만 REPL에 출력되지 않음

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findnext(A, CartesianIndex(1, 1))
CartesianIndex(2, 1)
```
