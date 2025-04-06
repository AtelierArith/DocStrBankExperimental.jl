```
potrs!(uplo, A, B)
```

`A * X = B`의 해를 찾습니다. 여기서 `A`는 `potrf!`에 의해 계산된 Cholesky 분해를 가진 대칭 또는 에르미트 양의 정부호 행렬입니다. `uplo = U`인 경우 `A`의 상부 Cholesky 분해가 계산되었습니다. `uplo = L`인 경우 `A`의 하부 Cholesky 분해가 계산되었습니다. `B`는 해 `X`로 덮어씌워집니다.
