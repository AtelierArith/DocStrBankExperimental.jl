```
findlast(predicate::Function, A)
```

`predicate`가 `true`를 반환하는 `A`의 마지막 요소의 인덱스 또는 키를 반환합니다. 그러한 요소가 없으면 `nothing`을 반환합니다.

인덱스 또는 키는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환되는 것과 동일한 유형입니다.

# 예제

```jldoctest
julia> A = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> findlast(isodd, A)
3

julia> findlast(x -> x > 5, A) # 아무것도 반환하지 않지만 REPL에 출력되지 않음

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> findlast(isodd, A)
CartesianIndex(2, 1)
```
