```
rowvals(A::AbstractSparseMatrixCSC)
```

`A`의 행 인덱스 벡터를 반환합니다. 반환된 벡터에 대한 수정은 `A`도 변형시킵니다. 행 인덱스가 내부적으로 어떻게 저장되는지에 대한 접근을 제공하는 것은 구조적 비영 값에 대해 반복하는 것과 함께 유용할 수 있습니다. [`nonzeros`](@ref) 및 [`nzrange`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> rowvals(A)
3-element Vector{Int64}:
 1
 2
 3
```
