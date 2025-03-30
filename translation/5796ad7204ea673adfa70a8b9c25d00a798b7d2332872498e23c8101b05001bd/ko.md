```
UInt
```

Sys.WORD_SIZE 비트 부호 없는 정수 타입, `UInt <: Unsigned <: Integer`.

[`Int`](@ref Int)와 마찬가지로, 별칭 `UInt`는 주어진 컴퓨터의 `Sys.WORD_SIZE` 값에 따라 `UInt32` 또는 `UInt64`를 가리킬 수 있습니다.

16진수로 출력 및 파싱됨: `UInt(15) === 0x000000000000000f`.
