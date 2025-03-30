```
findall(A)
```

벡터 `I`를 반환하여 `A`의 `true` 인덱스 또는 키를 제공합니다. `A`의 그러한 요소가 없으면 빈 배열을 반환합니다. 다른 종류의 값을 검색하려면 첫 번째 인수로 프레디케이트를 전달하십시오.

인덱스 또는 키는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환된 것과 동일한 유형입니다.

또한 참조: [`findfirst`](@ref), [`searchsorted`](@ref).

# 예제

```jldoctest
julia> A = [true, false, false, true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> findall(A)
2-element Vector{Int64}:
 1
 4

julia> A = [true false; false true]
2×2 Matrix{Bool}:
 1  0
 0  1

julia> findall(A)
2-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 2)

julia> findall(falses(3))
Int64[]
```
