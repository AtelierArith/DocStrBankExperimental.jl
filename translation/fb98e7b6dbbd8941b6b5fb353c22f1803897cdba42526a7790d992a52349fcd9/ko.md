```
@uint128_str str
```

`str`를 [`UInt128`](@ref)로 파싱합니다. 문자열이 유효한 정수가 아닐 경우 `ArgumentError`를 발생시킵니다.

# 예제

```
julia> uint128"123456789123"
0x00000000000000000000001cbe991a83

julia> uint128"-123456789123"
ERROR: LoadError: ArgumentError: invalid base 10 digit '-' in "-123456789123"
[...]
```
