```
trevc!(side, howmny, select, T, VL = similar(T), VR = similar(T))
```

상삼각 행렬 `T`의 고유 시스템을 찾습니다. `side = R`인 경우, 오른쪽 고유 벡터가 계산됩니다. `side = L`인 경우, 왼쪽 고유 벡터가 계산됩니다. `side = B`인 경우, 두 집합이 모두 계산됩니다. `howmny = A`인 경우, 모든 고유 벡터가 발견됩니다. `howmny = B`인 경우, 모든 고유 벡터가 발견되고 `VL`과 `VR`을 사용하여 역변환됩니다. `howmny = S`인 경우, `select`에 있는 값에 해당하는 고유 벡터만 계산됩니다.
