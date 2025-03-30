```
getindex(A, inds...)
```

인덱스 `inds`에 의해 선택된 배열 `A`의 하위 집합을 반환합니다.

각 인덱스는 [`Integer`](@ref), [`CartesianIndex`](@ref), [범위](@ref Base.AbstractRange), 또는 지원되는 인덱스의 [배열](@ref man-multi-dim-arrays)과 같은 [지원되는 인덱스 유형](@ref man-supported-index-types)일 수 있습니다. 특정 차원에서 모든 요소를 선택하기 위해 [:](@ref Base.Colon)를 사용할 수 있으며, 해당 인덱스가 `true`인 요소를 필터링하기 위해 불리언 배열(예: `Array{Bool}` 또는 [`BitArray`](@ref))을 사용할 수 있습니다.

`inds`가 여러 요소를 선택할 때, 이 함수는 새로 할당된 배열을 반환합니다. 복사 없이 여러 요소에 인덱싱하려면 대신 [`view`](@ref)를 사용하십시오.

자세한 내용은 [배열 인덱싱](@ref man-array-indexing) 매뉴얼 섹션을 참조하십시오.

# 예제

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> getindex(A, 1)
1

julia> getindex(A, [2, 1])
2-element Vector{Int64}:
 3
 1

julia> getindex(A, 2:4)
3-element Vector{Int64}:
 3
 2
 4

julia> getindex(A, 2, 1)
3

julia> getindex(A, CartesianIndex(2, 1))
3

julia> getindex(A, :, 2)
2-element Vector{Int64}:
 2
 4

julia> getindex(A, 2, :)
2-element Vector{Int64}:
 3
 4

julia> getindex(A, A .> 2)
2-element Vector{Int64}:
 3
 4
```
