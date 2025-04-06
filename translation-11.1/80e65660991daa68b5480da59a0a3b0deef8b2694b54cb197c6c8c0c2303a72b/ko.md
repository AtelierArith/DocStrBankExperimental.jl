```
hex2bytes(itr)
```

주어진 ASCII 코드의 iterable `itr`는 16진수 숫자의 시퀀스를 나타내며, 이진 표현에 해당하는 `Vector{UInt8}`의 바이트를 반환합니다: `itr`의 각 연속적인 16진수 숫자 쌍은 반환 벡터의 하나의 바이트 값을 제공합니다.

`itr`의 길이는 짝수여야 하며, 반환된 배열은 `itr`의 길이의 절반을 가집니다. 또한 [`hex2bytes!`](@ref) 인플레이스 버전과 [`bytes2hex`](@ref) 역함수도 참조하십시오.

!!! compat "Julia 1.7"
    `UInt8` 값을 생성하는 반복자를 사용하여 `hex2bytes`를 호출하려면 Julia 1.7 이상이 필요합니다. 이전 버전에서는 `hex2bytes`를 호출하기 전에 반복자를 `collect`할 수 있습니다.


# 예제

```jldoctest
julia> s = string(12345, base = 16)
"3039"

julia> hex2bytes(s)
2-element Vector{UInt8}:
 0x30
 0x39

julia> a = b"01abEF"
6-element Base.CodeUnits{UInt8, String}:
 0x30
 0x31
 0x61
 0x62
 0x45
 0x46

julia> hex2bytes(a)
3-element Vector{UInt8}:
 0x01
 0xab
 0xef
```
