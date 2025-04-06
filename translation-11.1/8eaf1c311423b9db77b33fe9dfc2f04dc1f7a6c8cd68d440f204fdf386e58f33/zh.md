```
ldiv!(A::Tridiagonal, B::AbstractVecOrMat) -> B
```

通过带部分主元的高斯消元法就地计算 `A \ B`，并将结果存储在 `B` 中，返回结果。在此过程中，`A` 的对角线也会被覆盖。

!!! compat "Julia 1.11"
    `ldiv!` 对于 `Tridiagonal` 左侧需要至少 Julia 1.11。

