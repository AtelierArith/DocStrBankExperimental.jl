```
ldiv!(A::Tridiagonal, B::AbstractVecOrMat) -> B
```

가우스 소거법을 사용하여 `A \ B`를 제자리에서 계산하고 결과를 `B`에 저장하며 결과를 반환합니다. 이 과정에서 `A`의 대각선도 덮어씌워집니다.

!!! compat "Julia 1.11"
    `Tridiagonal` 왼쪽 항에 대한 `ldiv!`는 최소한 Julia 1.11이 필요합니다.

