```
cholesky!(A::AbstractMatrix, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

与 [`cholesky`](@ref) 相同，但通过覆盖输入 `A` 来节省空间，而不是创建副本。如果因子分解产生的数字无法由 `A` 的元素类型表示，例如对于整数类型，将抛出 [`InexactError`](@ref) 异常。
