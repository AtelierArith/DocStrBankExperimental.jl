```
sygvd!(itype, jobz, uplo, A, B) -> (w, A, B)
```

대칭 행렬 `A`와 대칭 양의 정부호 행렬 `B`의 일반화된 고유값(`jobz = N`) 또는 고유값 및 고유벡터(`jobz = V`)를 찾습니다. `uplo = U`인 경우 `A`와 `B`의 상삼각형이 사용됩니다. `uplo = L`인 경우 `A`와 `B`의 하삼각형이 사용됩니다. `itype = 1`인 경우 해결해야 할 문제는 `A * x = lambda * B * x`입니다. `itype = 2`인 경우 해결해야 할 문제는 `A * B * x = lambda * x`입니다. `itype = 3`인 경우 해결해야 할 문제는 `B * A * x = lambda * x`입니다.
