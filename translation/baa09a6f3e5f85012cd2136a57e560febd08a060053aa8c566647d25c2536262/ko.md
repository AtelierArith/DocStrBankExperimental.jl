```
reinterpret(::Type{Out}, x::In)
```

이진 데이터의 타입 해석을 isbits 값 `x`에서 isbits 타입 `Out`으로 변경합니다. `Out`의 크기(패딩 무시)는 `x`의 타입과 동일해야 합니다. 예를 들어, `reinterpret(Float32, UInt32(7))`는 `UInt32(7)`에 해당하는 4바이트를 [`Float32`](@ref)로 해석합니다. `reinterpret(In, reinterpret(Out, x)) === x`임을 주의하세요.

```jldoctest
julia> reinterpret(Float32, UInt32(7))
1.0f-44

julia> reinterpret(NTuple{2, UInt8}, 0x1234)
(0x34, 0x12)

julia> reinterpret(UInt16, (0x34, 0x12))
0x1234

julia> reinterpret(Tuple{UInt16, UInt8}, (0x01, 0x0203))
(0x0301, 0x02)
```

!!! note
    패딩 처리 방식은 reinterpret(::DataType, ::AbstractArray)와 다릅니다.


!!! warning
    `Out`의 일부 비트 조합이 유효하지 않다고 간주되며, 그렇지 않으면 타입의 생성자 및 메서드에 의해 방지될 수 있는 경우 주의하십시오. 추가 검증 없이 예기치 않은 동작이 발생할 수 있습니다.

