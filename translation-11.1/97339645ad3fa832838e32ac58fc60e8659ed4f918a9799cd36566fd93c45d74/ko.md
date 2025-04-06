```
cis(A::AbstractMatrix)
```

정사각형 행렬 `A`의 `exp(im*A)`에 대한 더 효율적인 방법 (특히 `A`가 `Hermitian` 또는 실수 `Symmetric`인 경우).

또한 [`cispi`](@ref), [`sincos`](@ref), [`exp`](@ref)를 참조하십시오.

!!! compat "Julia 1.7"
    행렬과 함께 `cis`를 사용하는 지원이 Julia 1.7에 추가되었습니다.


# 예제

```jldoctest
julia> cis([π 0; 0 π]) ≈ -I
true
```
