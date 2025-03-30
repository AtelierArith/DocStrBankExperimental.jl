```
adjoint!(dest,src)
```

共轭转置数组 `src` 并将结果存储在预分配的数组 `dest` 中，`dest` 的大小应对应于 `(size(src,2),size(src,1))`。不支持就地转置，如果 `src` 和 `dest` 有重叠的内存区域，将会发生意外结果。

# 示例

```jldoctest
julia> A = [3+2im 9+2im; 8+7im  4+6im]
2×2 矩阵{复数{Int64}}:
 3+2im  9+2im
 8+7im  4+6im

julia> B = zeros(复数{Int64}, 2, 2)
2×2 矩阵{复数{Int64}}:
 0+0im  0+0im
 0+0im  0+0im

julia> adjoint!(B, A);

julia> B
2×2 矩阵{复数{Int64}}:
 3-2im  8-7im
 9-2im  4-6im

julia> A
2×2 矩阵{复数{Int64}}:
 3+2im  9+2im
 8+7im  4+6im
```
