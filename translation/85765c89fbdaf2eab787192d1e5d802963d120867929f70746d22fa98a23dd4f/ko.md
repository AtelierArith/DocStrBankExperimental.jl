```
trtrs!(uplo, trans, diag, A, B)
```

`A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), 또는 `adjoint(A) * X = B` (`trans = C`)를 해결합니다. 여기서 (상부는 `uplo = U`, 하부는 `uplo = L`) 삼각 행렬 `A`입니다. `diag = N`인 경우, `A`는 비단위 대각 요소를 가집니다. `diag = U`인 경우, `A`의 모든 대각 요소는 1입니다. `B`는 해 `X`로 덮어씌워집니다.
