```
diagm(v::AbstractVector)
diagm(m::Integer, n::Integer, v::AbstractVector)
```

构造一个以向量元素为对角线元素的矩阵。默认情况下，矩阵是方形的，其大小由 `length(v)` 给出，但可以通过将 `m,n` 作为第一个参数传递来指定非方形大小 `m`×`n`。

# 示例

```jldoctest
julia> diagm([1,2,3])
3×3 Matrix{Int64}:
 1  0  0
 0  2  0
 0  0  3
```
