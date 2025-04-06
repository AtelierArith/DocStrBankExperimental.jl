```
rot180(A, k)
```

将矩阵 `A` 旋转 180 度，整数 `k` 次。如果 `k` 是偶数，这相当于一个 `copy`。

# 示例

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rot180(a,1)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rot180(a,2)
2×2 Matrix{Int64}:
 1  2
 3  4
```
