```
gecon!(normtype, A, anorm)
```

행렬 `A`의 역 조건 수를 찾습니다. `normtype = I`인 경우, 조건 수는 무한 노름에서 찾습니다. `normtype = O` 또는 `1`인 경우, 조건 수는 1 노름에서 찾습니다. `A`는 `getrf!`의 결과여야 하며, `anorm`은 관련 노름에서의 `A`의 노름입니다.
