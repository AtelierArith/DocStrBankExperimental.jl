```
pstrf!(uplo, A, tol) -> (A, piv, rank, info)
```

양의 정부호 행렬 `A`의 (상부인 경우 `uplo = U`, 하부인 경우 `uplo = L`) 피벗된 콜레스키 분해를 사용자 설정 허용오차 `tol`로 계산합니다. `A`는 콜레스키 분해로 덮어씌워집니다.

`A`, 피벗 `piv`, `A`의 랭크, 그리고 `info` 코드를 반환합니다. `info = 0`이면 분해가 성공한 것입니다. `info = i > 0`이면 `A`가 부정적이거나 랭크가 결핍된 것입니다.
