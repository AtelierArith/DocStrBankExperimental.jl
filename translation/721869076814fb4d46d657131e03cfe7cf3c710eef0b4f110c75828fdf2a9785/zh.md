```
mul!(C, A, B, α, β) -> C
```

结合就地矩阵-矩阵或矩阵-向量乘加 $A B α + C β$。结果存储在 `C` 中，覆盖原有值。请注意，`C` 不能与 `A` 或 `B` 发生别名。

!!! compat "Julia 1.3"
    五个参数的 `mul!` 至少需要 Julia 1.3。


# 示例

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; C = [1.0 2.0; 3.0 4.0];

julia> α, β = 100.0, 10.0;

julia> mul!(C, A, B, α, β) === C
true

julia> C
2×2 Matrix{Float64}:
 310.0  320.0
 730.0  740.0

julia> C_original = [1.0 2.0; 3.0 4.0]; # C 的原始值的副本

julia> C == A * B * α + C_original * β
true
```
