```
cumprod!(y::AbstractVector, x::AbstractVector)
```

벡터 `x`의 누적 곱을 계산하여 결과를 `y`에 저장합니다. [`cumprod`](@ref)도 참조하세요.

!!! 경고     변형된 인수가 다른 인수와 메모리를 공유할 때 동작이 예기치 않게 될 수 있습니다.
