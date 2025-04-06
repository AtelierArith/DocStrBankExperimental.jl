```
gesvx!(fact, trans, A, AF, ipiv, equed, R, C, B) -> (X, equed, R, C, B, rcond, ferr, berr, work)
```

선형 방정식 `A * X = B` (`trans = N`), `transpose(A) * X = B` (`trans = T`), 또는 `adjoint(A) * X = B` (`trans = C`)를 `A`의 `LU` 분해를 사용하여 풉니다. `fact`는 `E`일 수 있으며, 이 경우 `A`는 균형을 맞추고 `AF`에 복사됩니다; `F`일 경우, 이전 `LU` 분해에서 `AF`와 `ipiv`가 입력으로 사용됩니다; 또는 `N`일 경우, `A`는 `AF`에 복사된 후 분해됩니다. `fact = F`인 경우, `equed`는 `N`일 수 있으며, 이는 `A`가 균형을 맞추지 않았음을 의미합니다; `R`은 `A`가 왼쪽에서 `Diagonal(R)`로 곱해졌음을 의미합니다; `C`는 `A`가 오른쪽에서 `Diagonal(C)`로 곱해졌음을 의미합니다; 또는 `B`는 `A`가 왼쪽에서 `Diagonal(R)`로 곱해지고 오른쪽에서 `Diagonal(C)`로 곱해졌음을 의미합니다. `fact = F`이고 `equed = R` 또는 `B`인 경우 `R`의 모든 요소는 양수여야 합니다. `fact = F`이고 `equed = C` 또는 `B`인 경우 `C`의 모든 요소는 양수여야 합니다.

해결책 `X`를 반환합니다; `equed`, 이는 `fact`가 `N`이 아닐 경우 출력이며 수행된 균형 조정을 설명합니다; `R`, 행 균형 대각선; `C`, 열 균형 대각선; `B`, 이는 균형을 맞춘 형태 `Diagonal(R)*B`로 덮어쓸 수 있습니다 (만약 `trans = N`이고 `equed = R,B`인 경우) 또는 `Diagonal(C)*B` (만약 `trans = T,C`이고 `equed = C,B`인 경우); `rcond`, 균형 조정 후 `A`의 역수 조건 수; `ferr`, `X`의 각 솔루션 벡터에 대한 전방 오차 한계; `berr`, `X`의 각 솔루션 벡터에 대한 전방 오차 한계; 및 `work`, 역수 피벗 성장 계수입니다.
