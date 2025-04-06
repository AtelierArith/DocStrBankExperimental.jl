```
permutedims(v::AbstractVector)
```

将向量 `v` 重塑为 `1 × length(v)` 行矩阵。与 [`transpose`](@ref) 的不同之处在于该操作不是递归的，这对于非数值值的数组尤其有用（递归的 `transpose` 可能会抛出错误）。

# 示例

与 `transpose` 不同，`permutedims` 可以用于任意非数值元素的向量，例如字符串：

```jldoctest
julia> permutedims(["a", "b", "c"])
1×3 Matrix{String}:
 "a"  "b"  "c"
```

对于数字向量，`permutedims(v)` 的工作方式与 `transpose(v)` 非常相似，除了返回类型不同（它使用 [`reshape`](@ref) 而不是 `LinearAlgebra.Transpose` 视图，尽管两者与原始数组 `v` 共享内存）：

```jldoctest; setup = :(using LinearAlgebra)
julia> v = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> p = permutedims(v)
1×4 Matrix{Int64}:
 1  2  3  4

julia> r = transpose(v)
1×4 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3  4

julia> p == r
true

julia> typeof(r)
Transpose{Int64, Vector{Int64}}

julia> p[1] = 5; r[2] = 6; # 修改 p 或 r 也会改变 v

julia> v # 与 p 和 r 共享内存
4-element Vector{Int64}:
 5
 6
 3
 4
```

然而，对于其元素本身是数值矩阵的向量，`permutedims` 产生的结果与 `transpose` 不同：

```jldoctest; setup = :(using LinearAlgebra)
julia> V = [[[1 2; 3 4]]; [[5 6; 7 8]]]
2-element Vector{Matrix{Int64}}:
 [1 2; 3 4]
 [5 6; 7 8]

julia> permutedims(V)
1×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [5 6; 7 8]

julia> transpose(V)
1×2 transpose(::Vector{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [5 7; 6 8]
```
