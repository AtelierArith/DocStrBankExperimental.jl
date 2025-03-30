```
trrfs!(uplo, trans, diag, A, B, X, Ferr, Berr) -> (Ferr, Berr)
```

`A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), `adjoint(A) * X = B` (`trans = C`)에 대한 해의 오차를 추정합니다. `side = L`인 경우, 또는 `trtrs!`를 사용하여 `X`를 계산한 후 오른쪽에 해당하는 `side = R`의 `X * A`에 대한 동등한 방정식입니다. `uplo = U`인 경우, `A`는 상삼각 행렬입니다. `uplo = L`인 경우, `A`는 하삼각 행렬입니다. `diag = N`인 경우, `A`는 비단위 대각 요소를 가집니다. `diag = U`인 경우, `A`의 모든 대각 요소는 1입니다. `Ferr`와 `Berr`는 선택적 입력입니다. `Ferr`는 전방 오차이고 `Berr`는 후방 오차로, 각 구성 요소별입니다.
