```
reinterpret(reshape, T, A::AbstractArray{S}) -> B
```

改变 `A` 的类型解释，同时消耗或添加一个“通道维度”。

如果 `sizeof(T) = n*sizeof(S)` 且 `n>1`，`A` 的第一维必须为大小 `n`，而 `B` 缺少 `A` 的第一维。相反，如果 `sizeof(S) = n*sizeof(T)` 且 `n>1`，`B` 将获得一个新的大小为 `n` 的第一维。如果 `sizeof(T) == sizeof(S)`，则维度不变。

!!! compat "Julia 1.6"
    此方法至少需要 Julia 1.6。


# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reinterpret(reshape, Complex{Int}, A)    # 结果是一个向量
2-element reinterpret(reshape, Complex{Int64}, ::Matrix{Int64}) with eltype Complex{Int64}:
 1 + 3im
 2 + 4im

julia> a = [(1,2,3), (4,5,6)]
2-element Vector{Tuple{Int64, Int64, Int64}}:
 (1, 2, 3)
 (4, 5, 6)

julia> reinterpret(reshape, Int, a)             # 结果是一个矩阵
3×2 reinterpret(reshape, Int64, ::Vector{Tuple{Int64, Int64, Int64}}) with eltype Int64:
 1  4
 2  5
 3  6
```
