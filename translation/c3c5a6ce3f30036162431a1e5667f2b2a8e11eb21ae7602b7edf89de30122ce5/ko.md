```
nonzeros(A)
```

희소 배열 `A`의 구조적 비영(非零) 값을 벡터로 반환합니다. 여기에는 희소 배열에 명시적으로 저장된 영(零) 값도 포함됩니다. 반환된 벡터는 `A`의 내부 비영 저장소를 직접 가리키며, 반환된 벡터에 대한 수정은 `A`도 변형시킵니다. [`rowvals`](@ref) 및 [`nzrange`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nonzeros(A)
3-element Vector{Int64}:
 2
 2
 2
```
