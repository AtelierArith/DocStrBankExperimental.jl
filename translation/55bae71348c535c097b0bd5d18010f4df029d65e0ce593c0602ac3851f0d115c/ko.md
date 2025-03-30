```
hermitianpart!(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

정사각형 행렬 `A`를 제자리에서 그 에르미트 부분 `(A + A') / 2`로 덮어쓰고, [`Hermitian(A, uplo)`](@ref)를 반환합니다. 실수 행렬 `A`의 경우, 이는 `A`의 대칭 부분으로도 알려져 있습니다.

상응하는 비제자리 연산에 대해서는 [`hermitianpart`](@ref)를 참조하십시오.

!!! compat "Julia 1.10"
    이 함수는 Julia 1.10 이상이 필요합니다.

