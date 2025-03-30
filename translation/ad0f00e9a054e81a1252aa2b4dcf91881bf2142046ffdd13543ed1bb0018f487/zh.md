```
isdiag(A) -> Bool
```

测试一个矩阵是否是对角矩阵，意思是除非 `i == j`，否则 `iszero(A[i,j])` 为真。请注意，`A` 不必是方阵；如果您还想检查这一点，您需要检查 `size(A, 1) == size(A, 2)`。

# 示例

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> isdiag(a)
false

julia> b = [im 0; 0 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  0+0im
 0+0im  0-1im

julia> isdiag(b)
true

julia> c = [1 0 0; 0 2 0]
2×3 Matrix{Int64}:
 1  0  0
 0  2  0

julia> isdiag(c)
true

julia> d = [1 0 0; 0 2 3]
2×3 Matrix{Int64}:
 1  0  0
 0  2  3

julia> isdiag(d)
false
```
