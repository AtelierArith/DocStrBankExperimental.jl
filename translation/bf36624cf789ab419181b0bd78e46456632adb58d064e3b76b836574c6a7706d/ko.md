```
Int128 <: Signed <: Integer
```

128비트 부호 있는 정수 타입입니다.

이러한 정수는 경고 없이 오버플로우되므로 `typemax(Int128) + Int128(1) < 0`입니다.

또한 [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref)를 참조하세요.
