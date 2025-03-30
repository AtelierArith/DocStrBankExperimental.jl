```
dropzeros(A::AbstractSparseMatrixCSC;)
```

`A`의 복사본을 생성하고 해당 복사본에서 저장된 수치 0을 제거합니다.

제자리 버전 및 알고리즘 정보는 [`dropzeros!`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> A = sparse([1, 2, 3], [1, 2, 3], [1.0, 0.0, 1.0])
3×3 SparseMatrixCSC{Float64, Int64} with 3 stored entries:
 1.0   ⋅    ⋅
  ⋅   0.0   ⋅
  ⋅    ⋅   1.0

julia> dropzeros(A)
3×3 SparseMatrixCSC{Float64, Int64} with 2 stored entries:
 1.0   ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅   1.0
```
