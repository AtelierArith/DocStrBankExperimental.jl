```
findprev(A, i)
```

`A`의 `true` 요소의 `i` 이전 또는 `i`를 포함한 이전 인덱스를 찾거나, 찾지 못한 경우 `nothing`을 반환합니다.

인덱스는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환되는 것과 동일한 유형입니다.

참고: [`findnext`](@ref), [`findfirst`](@ref), [`findall`](@ref).

# 예제

```jldoctest
julia> A = [false, false, true, true]
4-element Vector{Bool}:
 0
 0
 1
 1

julia> findprev(A, 3)
3

julia> findprev(A, 1) # nothing을 반환하지만 REPL에 출력되지 않음

julia> A = [false false; true true]
2×2 Matrix{Bool}:
 0  0
 1  1

julia> findprev(A, CartesianIndex(2, 1))
CartesianIndex(2, 1)
```
