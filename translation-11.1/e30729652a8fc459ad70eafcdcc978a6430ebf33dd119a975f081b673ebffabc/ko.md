```
gbtrs!(trans, kl, ku, m, AB, ipiv, B)
```

방정식 `AB * X = B`를 풉니다. `trans`는 `AB`의 방향을 결정합니다. `N`(전치 없음), `T`(전치), 또는 `C`(켤레 전치)일 수 있습니다. `kl`은 비영인 밴드를 포함하는 첫 번째 하부 대각선이고, `ku`는 하나를 포함하는 마지막 상부 대각선이며, `m`은 행렬 `AB`의 첫 번째 차원입니다. `ipiv`는 `gbtrf!`에서 반환된 피벗 벡터입니다. 벡터 또는 행렬 `X`를 반환하며, `B`를 제자리에서 덮어씁니다.
