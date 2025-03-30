```
ordschur(F::GeneralizedSchur, select::Union{Vector{Bool},BitVector}) -> F::GeneralizedSchur
```

행렬 쌍 `(A, B) = (Q*S*Z', Q*T*Z')`의 일반화된 슈르 분해 `F`를 논리 배열 `select`에 따라 재정렬하고 일반화된 슈르 객체 `F`를 반환합니다. 선택된 고유값은 `F.S`와 `F.T`의 주 대각선에 나타나며, 왼쪽 및 오른쪽 직교/유니타리 슈르 벡터도 재정렬되어 `(A, B) = F.Q*(F.S, F.T)*F.Z'`가 여전히 성립하고 `A`와 `B`의 일반화된 고유값을 `F.α./F.β`로 여전히 얻을 수 있습니다.
