```
Unsigned <: Integer
```

모든 부호 없는 정수에 대한 추상 슈퍼타입입니다.

내장된 부호 없는 정수는 16진수로 출력되며, 접두사 `0x`가 붙고 동일한 방식으로 입력할 수 있습니다.

# 예제

```
julia> typemax(UInt8)
0xff

julia> Int(0x00d)
13

julia> unsigned(true)
0x0000000000000001
```
