```
stev!(job, dv, ev) -> (dv, Zmat)
```

대칭 삼중 대각 행렬의 고유 시스템을 계산합니다. 여기서 `dv`는 대각선 요소이고 `ev`는 비대각선 요소입니다. `job = N`인 경우 고유값만 찾아서 `dv`에 반환합니다. `job = V`인 경우 고유벡터도 찾아서 `Zmat`에 반환합니다.
