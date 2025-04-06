```
trtrs!(uplo, trans, diag, A, B)
```

求解 `A * X = B` (`trans = N`)、`transpose(A) * X = B` (`trans = T`) 或 `adjoint(A) * X = B` (`trans = C`)，其中 `A` 是（如果 `uplo = U` 则为上三角，如果 `uplo = L` 则为下三角）矩阵。如果 `diag = N`，则 `A` 的对角元素为非单位元素。如果 `diag = U`，则 `A` 的所有对角元素均为一。`B` 被覆盖为解 `X`。
