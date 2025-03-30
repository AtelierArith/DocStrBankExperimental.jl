```
Int16 <: Signed <: Integer
```

16비트 부호 있는 정수 타입.

숫자 `n ∈ -32768:32767`을 나타냅니다. 이러한 정수는 경고 없이 오버플로우되므로 `typemax(Int16) + Int16(1) < 0`입니다.

또한 [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref)를 참조하세요.
