```
hermitianpart(A::AbstractMatrix, uplo::Symbol=:U) -> Hermitian
```

정사각형 행렬 `A`의 에르미트 부분을 반환합니다. 이는 `(A + A') / 2`로 정의되며, [`Hermitian`](@ref) 행렬로 반환됩니다. 실수 행렬 `A`의 경우, 이는 `A`의 대칭 부분으로도 알려져 있으며, 때때로 "연산자 실수 부분"이라고도 불립니다. 선택적 인수 `uplo`는 [`Hermitian`](@ref) 뷰의 해당 인수를 제어합니다. 실수 행렬의 경우, 후자는 [`Symmetric`](@ref) 뷰와 동등합니다.

상응하는 제자리 연산에 대해서는 [`hermitianpart!`](@ref)를 참조하십시오.

!!! compat "Julia 1.10"
    이 함수는 Julia 1.10 이상이 필요합니다.

