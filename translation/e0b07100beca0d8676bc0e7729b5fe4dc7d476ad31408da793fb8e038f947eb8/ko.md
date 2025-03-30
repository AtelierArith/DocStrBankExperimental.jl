```
GeneralizedSchur <: Factorization
```

두 행렬 `A`와 `B`의 일반화된 슈르 분해의 행렬 분해 유형입니다. 이는 [`schur(_, _)`](@ref) 함수의 반환 유형입니다.

`F::GeneralizedSchur`가 분해 객체인 경우, (준) 삼각 슈르 인자는 `F.S` 및 `F.T`를 통해 얻을 수 있으며, 왼쪽 유니타리/직교 슈르 벡터는 `F.left` 또는 `F.Q`를 통해, 오른쪽 유니타리/직교 슈르 벡터는 `F.right` 또는 `F.Z`를 통해 얻을 수 있습니다. 이때 `A=F.left*F.S*F.right'` 및 `B=F.left*F.T*F.right'`입니다. `A`와 `B`의 일반화된 고유값은 `F.α./F.β`를 통해 얻을 수 있습니다.

분해를 반복하면 구성 요소 `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α` 및 `F.β`가 생성됩니다.
