```
unsafe_write(io::IO, ref, nbytes::UInt)
```

`ref`에서 `nbytes`를 복사하여 `IO` 객체에 넣습니다(포인터로 변환됨).

하위 유형 `T<:IO`는 더 효율적인 구현을 제공하기 위해 다음 메서드 시그니처를 재정의하는 것이 권장됩니다: `unsafe_write(s::T, p::Ptr{UInt8}, n::UInt)`
