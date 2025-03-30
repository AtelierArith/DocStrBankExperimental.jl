```
cholesky!(A::AbstractMatrix, NoPivot(); check = true) -> Cholesky
```

与 [`cholesky`](@ref) 相同，但通过覆盖输入 `A` 来节省空间，而不是创建副本。如果因分解产生的数字无法用 `A` 的元素类型表示，例如对于整数类型，将抛出 [`InexactError`](@ref) 异常。

# 示例

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> cholesky!(A)
ERROR: InexactError: Int64(6.782329983125268)
Stacktrace:
[...]
```
