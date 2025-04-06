```
kron(A, B)
```

计算两个向量、矩阵或数字的克罗内克积。

对于实向量 `v` 和 `w`，克罗内克积与外积相关，通过 `kron(v,w) == vec(w * transpose(v))` 或 `w * transpose(v) == reshape(kron(v,w), (length(w), length(v)))`。注意 `v` 和 `w` 在这些表达式的左右两侧的顺序不同（由于列主存储）。对于复向量，外积 `w * v'` 也因 `v` 的共轭而有所不同。

# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> B = [im 1; 1 -im]
2×2 Matrix{Complex{Int64}}:
 0+1im  1+0im
 1+0im  0-1im

julia> kron(A, B)
4×4 Matrix{Complex{Int64}}:
 0+1im  1+0im  0+2im  2+0im
 1+0im  0-1im  2+0im  0-2im
 0+3im  3+0im  0+4im  4+0im
 3+0im  0-3im  4+0im  0-4im

julia> v = [1, 2]; w = [3, 4, 5];

julia> w*transpose(v)
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10

julia> reshape(kron(v,w), (length(w), length(v)))
3×2 Matrix{Int64}:
 3   6
 4   8
 5  10
```
