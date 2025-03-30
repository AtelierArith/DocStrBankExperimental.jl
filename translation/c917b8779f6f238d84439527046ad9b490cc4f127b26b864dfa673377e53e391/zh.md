```
issuccess(F::Factorization)
```

测试矩阵的因式分解是否成功。

!!! compat "Julia 1.6"
    `issuccess(::CholeskyPivoted)` 需要 Julia 1.6 或更高版本。


# 示例

```jldoctest
julia> F = cholesky([1 0; 0 1]);

julia> issuccess(F)
true
```
