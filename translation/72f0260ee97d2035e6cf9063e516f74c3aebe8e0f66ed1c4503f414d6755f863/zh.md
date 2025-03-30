```
vcat(A...)
```

垂直连接数组或数字。等价于 [`cat`](@ref)`(A...; dims=1)`，以及语法 `[a; b; c]`。

要连接一个大型数组向量，`reduce(vcat, A)` 在 `A isa AbstractVector{<:AbstractVecOrMat}` 时调用高效方法，而不是逐对处理。

另请参见 [`hcat`](@ref)，[`Iterators.flatten`](@ref)，[`stack`](@ref)。

# 示例

```jldoctest
julia> v = vcat([1,2], [3,4])
4-element Vector{Int64}:
 1
 2
 3
 4

julia> v == vcat(1, 2, [3,4])  # 接受数字
true

julia> v == [1; 2; [3,4]]  # 相同操作的语法
true

julia> summary(ComplexF64[1; 2; [3,4]])  # 提供元素类型的语法
"4-element Vector{ComplexF64}"

julia> vcat(range(1, 2, length=3))  # 收集惰性范围
3-element Vector{Float64}:
 1.0
 1.5
 2.0

julia> two = ([10, 20, 30]', Float64[4 5 6; 7 8 9])  # 行向量和矩阵
([10 20 30], [4.0 5.0 6.0; 7.0 8.0 9.0])

julia> vcat(two...)
3×3 Matrix{Float64}:
 10.0  20.0  30.0
  4.0   5.0   6.0
  7.0   8.0   9.0

julia> vs = [[1, 2], [3, 4], [5, 6]];

julia> reduce(vcat, vs)  # 比 vcat(vs...) 更高效
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> ans == collect(Iterators.flatten(vs))
true
```
