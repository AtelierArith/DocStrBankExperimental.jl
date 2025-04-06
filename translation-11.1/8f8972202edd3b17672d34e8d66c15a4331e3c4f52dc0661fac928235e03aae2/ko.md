```
bitstring(n)
```

원시 타입의 리터럴 비트 표현을 제공하는 문자열입니다.

또한 [`count_ones`](@ref), [`count_zeros`](@ref), [`digits`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> bitstring(Int32(4))
"00000000000000000000000000000100"

julia> bitstring(2.2)
"0100000000000001100110011001100110011001100110011001100110011010"
```
