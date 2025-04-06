```
findlast(A)
```

`A`에서 마지막 `true` 값의 인덱스 또는 키를 반환합니다. `A`에 `true` 값이 없으면 `nothing`을 반환합니다.

인덱스 또는 키는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환되는 것과 동일한 유형입니다.

참고: [`findfirst`](@ref), [`findprev`](@ref), [`findall`](@ref).

# 예제

```jldoctest
julia> A = [true, false, true, false]
4-element Vector{Bool}:
 1
 0
 1
 0

julia> findlast(A)
3

julia> A = falses(2,2);

julia> findlast(A) # 아무것도 반환하지 않지만 REPL에 출력되지 않음

julia> A = [true false; true false]
2×2 Matrix{Bool}:
 1  0
 1  0

julia> findlast(A)
CartesianIndex(2, 1)
```
