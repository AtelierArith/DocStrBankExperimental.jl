```
potrf!(uplo, A)
```

양의 정부호 행렬 `A`의 Cholesky(위쪽은 `uplo = U`, 아래쪽은 `uplo = L`) 분해를 계산합니다. `A`는 덮어쓰여지며 정보 코드와 함께 반환됩니다.
