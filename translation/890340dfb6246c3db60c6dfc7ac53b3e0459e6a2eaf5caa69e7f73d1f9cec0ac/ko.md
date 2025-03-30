```
gemqrt!(side, trans, V, T, C)
```

`Q * C`를 계산합니다 (`trans = N`), `transpose(Q) * C` (`trans = T`), `adjoint(Q) * C` (`trans = C`)는 `side = L`에 대해 또는 `side = R`에 대해 `geqrt!`를 사용하여 계산된 `A`의 `QR` 분해에서 `Q`를 사용하여 동일한 오른쪽 곱셈을 수행합니다. `C`는 덮어씌워집니다.
