```
nzrange(A::AbstractSparseMatrixCSC, col::Integer)
```

返回稀疏矩阵列的结构非零值的索引范围。结合 [`nonzeros`](@ref) 和 [`rowvals`](@ref)，这允许方便地遍历稀疏矩阵：

```
A = sparse(I,J,V)
rows = rowvals(A)
vals = nonzeros(A)
m, n = size(A)
for j = 1:n
   for i in nzrange(A, j)
      row = rows[i]
      val = vals[i]
      # 执行稀疏魔法...
   end
end
```

!!! warning
    向矩阵添加或移除非零元素可能会使 `nzrange` 无效，在迭代时不应修改矩阵。

