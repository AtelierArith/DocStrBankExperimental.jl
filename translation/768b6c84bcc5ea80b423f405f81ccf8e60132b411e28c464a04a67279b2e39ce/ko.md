```
transpose(F::Factorization)
```

팩토리제이션 `F`의 지연 전치. 기본적으로 [`TransposeFactorization`](@ref)를 반환하지만, 실수 `eltype`을 가진 `Factorization`의 경우 [`AdjointFactorization`](@ref)를 반환합니다.
