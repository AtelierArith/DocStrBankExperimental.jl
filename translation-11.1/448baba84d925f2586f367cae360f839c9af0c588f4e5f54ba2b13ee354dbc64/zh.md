```
gesvx!(fact, trans, A, AF, ipiv, equed, R, C, B) -> (X, equed, R, C, B, rcond, ferr, berr, work)
```

求解线性方程 `A * X = B` (`trans = N`)、`transpose(A) * X = B` (`trans = T`) 或 `adjoint(A) * X = B` (`trans = C`)，使用 `A` 的 `LU` 分解。`fact` 可以是 `E`，在这种情况下 `A` 将被平衡并复制到 `AF`；可以是 `F`，在这种情况下 `AF` 和 `ipiv` 来自先前的 `LU` 分解作为输入；或者是 `N`，在这种情况下 `A` 将被复制到 `AF` 然后进行分解。如果 `fact = F`，`equed` 可以是 `N`，表示 `A` 尚未平衡；`R`，表示 `A` 从左侧乘以 `Diagonal(R)`；`C`，表示 `A` 从右侧乘以 `Diagonal(C)`；或 `B`，表示 `A` 从左侧乘以 `Diagonal(R)` 并从右侧乘以 `Diagonal(C)`。如果 `fact = F` 且 `equed = R` 或 `B`，则 `R` 的所有元素必须为正。如果 `fact = F` 且 `equed = C` 或 `B`，则 `C` 的所有元素必须为正。

返回解 `X`；`equed`，如果 `fact` 不是 `N`，则为输出，描述所执行的平衡；`R`，行平衡对角线；`C`，列平衡对角线；`B`，可能会被其平衡形式 `Diagonal(R)*B`（如果 `trans = N` 且 `equed = R,B`）或 `Diagonal(C)*B`（如果 `trans = T,C` 且 `equed = C,B`）覆盖；`rcond`，平衡后 `A` 的倒数条件数；`ferr`，每个解向量在 `X` 中的前向误差界限；`berr`，每个解向量在 `X` 中的前向误差界限；以及 `work`，倒数主元增长因子。
