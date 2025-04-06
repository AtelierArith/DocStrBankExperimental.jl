```
mul!(Y, A, B) -> Y
```

计算矩阵-矩阵或矩阵-向量乘积 $A B$ 并将结果存储在 `Y` 中，覆盖 `Y` 的现有值。请注意，`Y` 不能与 `A` 或 `B` 发生别名。

# 示例

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; Y = similar(B);

julia> mul!(Y, A, B) === Y
true

julia> Y
2×2 Matrix{Float64}:
 3.0  3.0
 7.0  7.0

julia> Y == A * B
true
```

# 实现

对于自定义矩阵和向量类型，建议实现 5 个参数的 `mul!`，而不是直接实现 3 个参数的 `mul!`。
