```
Char(c::Union{Number,AbstractChar})
```

`Char`는 Julia에서 문자의 기본 표현인 32비트 [`AbstractChar`](@ref) 타입입니다. `Char`는 `'x'`와 같은 문자 리터럴에 사용되는 타입이며, [`String`](@ref)의 요소 타입이기도 합니다.

`String`에 저장된 임의의 바이트 스트림을 손실 없이 표현하기 위해, `Char` 값은 유니코드 코드 포인트로 변환할 수 없는 정보를 저장할 수 있습니다 — 그러한 `Char`를 `UInt32`로 변환하면 오류가 발생합니다. [`isvalid(c::Char)`](@ref) 함수는 `c`가 유효한 유니코드 문자를 나타내는지 여부를 쿼리하는 데 사용할 수 있습니다.
