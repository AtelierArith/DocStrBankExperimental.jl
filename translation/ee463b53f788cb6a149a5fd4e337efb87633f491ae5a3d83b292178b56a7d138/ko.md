```
findall(f::Function, A)
```

함수 `f(A[I])`가 `true`를 반환하는 `A`의 인덱스 또는 키의 벡터 `I`를 반환합니다. `A`의 그러한 요소가 없으면 빈 배열을 반환합니다.

인덱스 또는 키는 [`keys(A)`](@ref) 및 [`pairs(A)`](@ref)에서 반환된 것과 동일한 유형입니다.

# 예제

```jldoctest
julia> x = [1, 3, 4]
3-element Vector{Int64}:
 1
 3
 4

julia> findall(isodd, x)
2-element Vector{Int64}:
 1
 2

julia> A = [1 2 0; 3 4 0]
2×3 Matrix{Int64}:
 1  2  0
 3  4  0
julia> findall(isodd, A)
2-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 1)

julia> findall(!iszero, A)
4-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 1)
 CartesianIndex(1, 2)
 CartesianIndex(2, 2)

julia> d = Dict(:A => 10, :B => -1, :C => 0)
Dict{Symbol, Int64} with 3 entries:
  :A => 10
  :B => -1
  :C => 0

julia> findall(x -> x >= 0, d)
2-element Vector{Symbol}:
 :A
 :C

```
