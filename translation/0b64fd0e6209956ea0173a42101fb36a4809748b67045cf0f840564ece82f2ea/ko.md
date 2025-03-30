```
nextfloat(x::AbstractFloat)
```

같은 유형의 가장 작은 부동 소수점 숫자 `y`를 반환합니다. 단, `x < y`를 만족해야 합니다. 만약 그러한 `y`가 존재하지 않는 경우(예: `x`가 `Inf` 또는 `NaN`인 경우), `x`를 반환합니다.

또한 참조: [`prevfloat`](@ref), [`eps`](@ref), [`issubnormal`](@ref).
