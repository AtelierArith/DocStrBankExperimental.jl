```
norm(A, p::Real=2)
```

对于任何可迭代容器 `A`（包括任意维度的数组）中的数字（或任何定义了 `norm` 的元素类型），计算 `p`-范数（默认为 `p=2`），就好像 `A` 是一个对应长度的向量。

`p`-范数定义为

$$
\|A\|_p = \left( \sum_{i=1}^n | a_i | ^p \right)^{1/p}
$$

其中 $a_i$ 是 `A` 的条目，$| a_i |$ 是 [`norm`](@ref) 的 `a_i`，$n$ 是 `A` 的长度。由于 `p`-范数是使用 `A` 的条目的 [`norm`](@ref) 计算的，因此当 `p != 2` 时，向量的向量的 `p`-范数通常与其作为块向量的解释不兼容。

`p` 可以取任何数值（尽管并非所有值都产生数学上有效的向量范数）。特别地，`norm(A, Inf)` 返回 `abs.(A)` 中的最大值，而 `norm(A, -Inf)` 返回最小值。如果 `A` 是一个矩阵且 `p=2`，那么这等同于 Frobenius 范数。

第二个参数 `p` 不一定是 `norm` 接口的一部分，即自定义类型可能只实现 `norm(A)` 而没有第二个参数。

使用 [`opnorm`](@ref) 计算矩阵的算子范数。

# 示例

```jldoctest
julia> v = [3, -2, 6]
3-element Vector{Int64}:
  3
 -2
  6

julia> norm(v)
7.0

julia> norm(v, 1)
11.0

julia> norm(v, Inf)
6.0

julia> norm([1 2 3; 4 5 6; 7 8 9])
16.881943016134134

julia> norm([1 2 3 4 5 6 7 8 9])
16.881943016134134

julia> norm(1:9)
16.881943016134134

julia> norm(hcat(v,v), 1) == norm(vcat(v,v), 1) != norm([v,v], 1)
true

julia> norm(hcat(v,v), 2) == norm(vcat(v,v), 2) == norm([v,v], 2)
true

julia> norm(hcat(v,v), Inf) == norm(vcat(v,v), Inf) != norm([v,v], Inf)
true
```
