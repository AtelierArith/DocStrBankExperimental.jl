```
unsafe_read(io::IO, ref, nbytes::UInt)
```

`IO` 스트림 객체에서 `ref`로 `nbytes`를 복사합니다(포인터로 변환됨).

서브타입 `T<:IO`는 더 효율적인 구현을 제공하기 위해 다음 메서드 시그니처를 재정의하는 것이 권장됩니다: `unsafe_read(s::T, p::Ptr{UInt8}, n::UInt)`
