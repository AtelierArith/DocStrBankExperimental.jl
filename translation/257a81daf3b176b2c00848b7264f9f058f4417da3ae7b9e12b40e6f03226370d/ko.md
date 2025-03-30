```
gttrs!(trans, dl, d, du, du2, ipiv, B)
```

방정식 `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), 또는 `adjoint(A) * X = B` (`trans = C`)를 `gttrf!`에 의해 계산된 `LU` 분해를 사용하여 풉니다. `B`는 해 `X`로 덮어씌워집니다.
