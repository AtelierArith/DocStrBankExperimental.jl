```
findfirst(A)
```

`A`에서 첫 번째 `true` 값의 인덱스 또는 키를 반환합니다. 그러한 값이 발견되지 않으면 `nothing`을 반환합니다. 다른 종류의 값을 검색하려면 첫 번째 인수로 술어를 전달하십시오.

인덱스 또는 키는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환되는 것과 동일한 유형입니다.

참고: [`findall`](@ref), [`findnext`](@ref), [`findlast`](@ref), [`searchsortedfirst`](@ref).

# 예제

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findfirst(A)
3

julia> findfirst(falses(3)) # 아무것도 반환하지 않지만 REPL에 출력되지 않음

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findfirst(A)
CartesianIndex(2, 1)
```
