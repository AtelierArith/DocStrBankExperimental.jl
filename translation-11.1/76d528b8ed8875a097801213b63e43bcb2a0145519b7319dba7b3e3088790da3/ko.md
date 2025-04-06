```
stebz!(range, order, vl, vu, il, iu, abstol, dv, ev) -> (dv, iblock, isplit)
```

대칭 삼중 대각 행렬의 고유값을 계산합니다. 여기서 `dv`는 대각선 요소이고 `ev`는 비대각선 요소입니다. `range = A`인 경우 모든 고유값이 찾아집니다. `range = V`인 경우 반개방 구간 `(vl, vu]` 내의 고유값이 찾아집니다. `range = I`인 경우 인덱스가 `il`과 `iu` 사이에 있는 고유값이 찾아집니다. `order = B`인 경우 고유값이 블록 내에서 정렬됩니다. `order = E`인 경우 모든 블록에 걸쳐 정렬됩니다. `abstol`은 수렴을 위한 허용 오차로 설정할 수 있습니다.
