```
syevr!(jobz, range, uplo, A, vl, vu, il, iu, abstol) -> (W, Z)
```

대칭 행렬 `A`의 고유값(`jobz = N`) 또는 고유값과 고유벡터(`jobz = V`)를 찾습니다. `uplo = U`인 경우 `A`의 상삼각형이 사용됩니다. `uplo = L`인 경우 `A`의 하삼각형이 사용됩니다. `range = A`인 경우 모든 고유값이 찾습니다. `range = V`인 경우 반열린 구간 `(vl, vu]`에 있는 고유값이 찾습니다. `range = I`인 경우 인덱스가 `il`과 `iu` 사이에 있는 고유값이 찾습니다. `abstol`은 수렴을 위한 허용오차로 설정할 수 있습니다.

고유값은 `W`에, 고유벡터는 `Z`에 반환됩니다.
