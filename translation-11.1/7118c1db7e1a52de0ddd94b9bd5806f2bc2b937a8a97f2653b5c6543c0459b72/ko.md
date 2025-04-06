```
geevx!(balanc, jobvl, jobvr, sense, A) -> (A, w, VL, VR, ilo, ihi, scale, abnrm, rconde, rcondv)
```

`A`의 고유 시스템을 행렬 균형을 사용하여 찾습니다. `jobvl = N`인 경우 `A`의 왼쪽 고유 벡터는 계산되지 않습니다. `jobvr = N`인 경우 `A`의 오른쪽 고유 벡터는 계산되지 않습니다. `jobvl = V` 또는 `jobvr = V`인 경우 해당 고유 벡터가 계산됩니다. `balanc = N`인 경우 균형 조정이 수행되지 않습니다. `balanc = P`인 경우 `A`는 순열되지만 스케일링되지 않습니다. `balanc = S`인 경우 `A`는 스케일링되지만 순열되지 않습니다. `balanc = B`인 경우 `A`는 순열되고 스케일링됩니다. `sense = N`인 경우 역 조건 수가 계산되지 않습니다. `sense = E`인 경우 고유값에 대해서만 역 조건 수가 계산됩니다. `sense = V`인 경우 오른쪽 고유 벡터에 대해서만 역 조건 수가 계산됩니다. `sense = B`인 경우 오른쪽 고유 벡터와 고유 벡터에 대해 역 조건 수가 계산됩니다. `sense = E,B`인 경우 오른쪽 및 왼쪽 고유 벡터가 계산되어야 합니다.
