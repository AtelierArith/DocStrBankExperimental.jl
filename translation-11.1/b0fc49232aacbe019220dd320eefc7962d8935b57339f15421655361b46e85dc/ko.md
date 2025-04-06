```
ggev!(jobvl, jobvr, A, B) -> (alpha, beta, vl, vr)
```

`A`와 `B`의 일반화된 고유 분해를 찾습니다. `jobvl = N`인 경우 왼쪽 고유 벡터는 계산되지 않습니다. `jobvr = N`인 경우 오른쪽 고유 벡터는 계산되지 않습니다. `jobvl = V` 또는 `jobvr = V`인 경우 해당 고유 벡터가 계산됩니다.
