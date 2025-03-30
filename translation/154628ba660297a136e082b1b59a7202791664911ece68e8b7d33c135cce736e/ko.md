```
getrs!(trans, A, ipiv, B)
```

선형 방정식 `A * X = B`, `transpose(A) * X = B`, 또는 `adjoint(A) * X = B`를 정사각형 행렬 `A`에 대해 풉니다. 해결책으로 행렬/벡터 `B`를 제자리에서 수정합니다. `A`는 `getrf!`에서의 `LU` 분해이며, `ipiv`는 피벗 정보입니다. `trans`는 `N`(수정 없음), `T`(전치), 또는 `C`(켤레 전치) 중 하나일 수 있습니다.
