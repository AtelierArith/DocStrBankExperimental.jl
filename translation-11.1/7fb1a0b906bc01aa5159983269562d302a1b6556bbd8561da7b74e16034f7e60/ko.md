```
Int
```

Sys.WORD_SIZE 비트 부호 있는 정수 타입, `Int <: Signed <: Integer <: Real`.

이는 대부분의 정수 리터럴의 기본 타입이며, `Sys.WORD_SIZE`에 따라 `Int32` 또는 `Int64`의 별칭입니다. 이는 [`length`](@ref)와 같은 함수가 반환하는 타입이며, 배열 인덱싱을 위한 표준 타입입니다.

정수는 경고 없이 오버플로우되므로, `typemax(Int) + 1 < 0` 및 `10^19 < 0`입니다. 오버플로우는 [`BigInt`](@ref)를 사용하여 피할 수 있습니다. 매우 큰 정수 리터럴은 더 넓은 타입을 사용하며, 예를 들어 `10_000_000_000_000_000_000 isa Int128`입니다.

정수 나눗셈은 [`div`](@ref) 별칭 `÷`이며, 정수에 대해 작동하는 [`/`](@ref)는 [`Float64`](@ref)를 반환합니다.

또한 [`Int64`](@ref), [`widen`](@ref), [`typemax`](@ref), [`bitstring`](@ref)를 참조하십시오.
