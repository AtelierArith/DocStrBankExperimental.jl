```
sytrf!(uplo, A, ipiv) -> (A, ipiv, info)
```

대칭 행렬 `A`의 Bunch-Kaufman 분해를 계산합니다. `uplo = U`인 경우 `A`의 상단 절반이 저장됩니다. `uplo = L`인 경우 하단 절반이 저장됩니다.

분해로 덮어쓴 `A`, 피벗 벡터 `ipiv`, 그리고 비음수 정수인 오류 코드 `info`를 반환합니다. `info`가 양수인 경우 행렬이 특이하며 분해의 대각선 부분이 정확히 `info` 위치에서 0입니다.
