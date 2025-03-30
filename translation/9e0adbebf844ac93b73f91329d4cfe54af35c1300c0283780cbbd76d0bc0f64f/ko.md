```
findnz(A::SparseMatrixCSC)
```

희소 행렬 `A`에 저장된 ("구조적으로 비영(zero)") 값의 행 및 열 인덱스인 튜플 `(I, J, V)`를 반환합니다. 여기서 `I`와 `J`는 인덱스이고, `V`는 값의 벡터입니다.

# 예제

```jldoctest
julia> A = sparse([1 2 0; 0 0 3; 0 4 0])
3×3 SparseMatrixCSC{Int64, Int64} with 4 stored entries:
 1  2  ⋅
 ⋅  ⋅  3
 ⋅  4  ⋅

julia> findnz(A)
([1, 1, 3, 2], [1, 2, 2, 3], [1, 2, 4, 3])
```
