```
gges3!(jobvsl, jobvsr, A, B) -> (A, B, alpha, beta, vsl, vsr)
```

일반화된 고유값, 일반화된 슈르 형식, 왼쪽 슈르 벡터(`jobsvl = V`), 또는 오른쪽 슈르 벡터(`jobvsr = V`)를 차단된 알고리즘을 사용하여 `A`와 `B`의 계산합니다. 이 함수는 LAPACK 3.6.0이 필요합니다.

일반화된 고유값은 `alpha`와 `beta`에 반환됩니다. 왼쪽 슈르 벡터는 `vsl`에 반환되고 오른쪽 슈르 벡터는 `vsr`에 반환됩니다.
