```
trtrs!(uplo, trans, diag, A, B)
```

`A * X = B`（`trans = N`）、`transpose(A) * X = B`（`trans = T`）、または`adjoint(A) * X = B`（`trans = C`）を解きます。ここで、`A`は（`uplo = U`の場合は上三角、`uplo = L`の場合は下三角）三角行列です。`diag = N`の場合、`A`は単位でない対角要素を持ちます。`diag = U`の場合、`A`のすべての対角要素は1です。`B`は解`X`で上書きされます。
