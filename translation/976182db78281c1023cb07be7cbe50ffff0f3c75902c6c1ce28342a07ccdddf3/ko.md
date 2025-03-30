```
nzrange(A::AbstractSparseMatrixCSC, col::Integer)
```

희소 행렬 열의 구조적 비영(非零) 값에 대한 인덱스 범위를 반환합니다. [`nonzeros`](@ref) 및 [`rowvals`](@ref)와 함께 사용하면 희소 행렬을 편리하게 반복(iterate)할 수 있습니다:

```
A = sparse(I,J,V)
rows = rowvals(A)
vals = nonzeros(A)
m, n = size(A)
for j = 1:n
   for i in nzrange(A, j)
      row = rows[i]
      val = vals[i]
      # 희소 마법 수행...
   end
end
```

!!! 경고     행렬에 비영(非零) 요소를 추가하거나 제거하면 `nzrange`가 무효화될 수 있으므로, 반복(iterating)하는 동안 행렬을 변경해서는 안 됩니다.
