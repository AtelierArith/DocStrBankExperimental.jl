```
bytes2hex(itr) -> String
bytes2hex(io::IO, itr)
```

바이트의 반복자 `itr`를 16진수 문자열 표현으로 변환합니다. `bytes2hex(itr)`를 통해 `String`을 반환하거나 `bytes2hex(io, itr)`를 통해 문자열을 `io` 스트림에 씁니다. 16진수 문자는 모두 소문자입니다.

!!! compat "Julia 1.7"
    임의의 반복자가 `UInt8` 값을 생성하는 경우 `bytes2hex`를 호출하려면 Julia 1.7 이상이 필요합니다. 이전 버전에서는 `bytes2hex`를 호출하기 전에 반복자를 `collect`할 수 있습니다.


# 예제

```jldoctest
julia> a = string(12345, base = 16)
"3039"

julia> b = hex2bytes(a)
2-element Vector{UInt8}:
 0x30
 0x39

julia> bytes2hex(b)
"3039"
```
