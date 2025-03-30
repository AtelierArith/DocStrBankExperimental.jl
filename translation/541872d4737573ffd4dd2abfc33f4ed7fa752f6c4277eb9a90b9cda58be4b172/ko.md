```
ordschur(F::Schur, select::Union{Vector{Bool},BitVector}) -> F::Schur
```

행렬 `A = Z*T*Z'`의 Schur 분해 `F`를 논리 배열 `select`에 따라 재정렬하여 재정렬된 분해 `F` 객체를 반환합니다. 선택된 고유값은 `F.Schur`의 주 대각선에 나타나며, 해당하는 `F.vectors`의 선두 열은 해당하는 오른쪽 불변 부분공간의 직교/유니타리 기저를 형성합니다. 실수의 경우, 복소수 켤레 쌍의 고유값은 `select`를 통해 모두 포함되거나 모두 제외되어야 합니다.
