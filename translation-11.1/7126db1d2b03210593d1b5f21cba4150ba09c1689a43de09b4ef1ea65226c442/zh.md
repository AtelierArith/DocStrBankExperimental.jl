```
trtri!(uplo, diag, A)
```

找到（如果 `uplo = U` 则为上三角，如果 `uplo = L` 则为下三角）矩阵 `A` 的逆。如果 `diag = N`，则 `A` 具有非单位对角元素。如果 `diag = U`，则 `A` 的所有对角元素均为一。`A` 被其逆所覆盖。
