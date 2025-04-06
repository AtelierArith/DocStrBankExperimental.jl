```
Int32 <: Signed <: Integer
```

32비트 부호 있는 정수 유형입니다.

이러한 정수는 경고 없이 오버플로우되므로 `typemax(Int32) + Int32(1) < 0`입니다.

또한 [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref)를 참조하십시오.
