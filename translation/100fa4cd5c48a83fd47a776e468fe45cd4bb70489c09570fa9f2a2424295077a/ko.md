```
Int64 <: Signed <: Integer
```

64비트 부호 있는 정수형.

이러한 정수는 경고 없이 오버플로우되므로 `typemax(Int64) + Int64(1) < 0`입니다.

또한 [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref)를 참조하세요.
