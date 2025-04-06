```
issuccess(F::LU; allowsingular = false)
```

测试矩阵的 LU 分解是否成功。默认情况下，产生有效但秩不足的 U 因子的分解被视为失败。通过传递 `allowsingular = true` 可以更改此行为。

!!! compat "Julia 1.11"
    `allowsingular` 关键字参数是在 Julia 1.11 中添加的。


# 示例

```jldoctest
julia> F = lu([1 2; 1 2], check = false);

julia> issuccess(F)
false

julia> issuccess(F, allowsingular = true)
true
```
