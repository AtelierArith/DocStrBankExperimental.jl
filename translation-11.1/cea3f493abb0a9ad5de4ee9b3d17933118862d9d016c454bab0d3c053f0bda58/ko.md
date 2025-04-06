```
findprev(predicate::Function, A, i)
```

`predicate`가 `true`를 반환하는 `A`의 요소에 대해 `i` 이전 또는 `i`를 포함한 이전 인덱스를 찾거나, 찾지 못한 경우 `nothing`을 반환합니다. 이는 [`getindex`](@ref), [`keys(A)`](@ref), 및 [`nextind`](@ref)를 지원하는 배열, 문자열 및 대부분의 다른 컬렉션에서 작동합니다.

인덱스는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환된 것과 동일한 유형입니다.

# 예제

```jldoctest
julia> A = [4, 6, 1, 2]
4-element Vector{Int64}:
 4
 6
 1
 2

julia> findprev(isodd, A, 1) # 아무것도 반환하지 않지만 REPL에 출력되지 않음

julia> findprev(isodd, A, 3)
3

julia> A = [4 6; 1 2]
2×2 Matrix{Int64}:
 4  6
 1  2

julia> findprev(isodd, A, CartesianIndex(1, 2))
CartesianIndex(2, 1)

julia> findprev(isspace, "a b c", 3)
2
```
