```
gges!(jobvsl, jobvsr, A, B) -> (A, B, alpha, beta, vsl, vsr)
```

일반화 고유값, 일반화 슈르 형식, 왼쪽 슈르 벡터(`jobsvl = V`), 또는 오른쪽 슈르 벡터(`jobvsr = V`)를 `A`와 `B`의 경우 계산합니다.

일반화 고유값은 `alpha`와 `beta`에 반환됩니다. 왼쪽 슈르 벡터는 `vsl`에 반환되고 오른쪽 슈르 벡터는 `vsr`에 반환됩니다.
