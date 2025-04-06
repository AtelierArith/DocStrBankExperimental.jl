```
@big_str str
```

문자열을 [`BigInt`](@ref) 또는 [`BigFloat`](@ref)로 파싱하고, 문자열이 유효한 숫자가 아닐 경우 `ArgumentError`를 발생시킵니다. 정수의 경우 `_`는 문자열에서 구분자로 허용됩니다.

# 예제

```jldoctest
julia> big"123_456"
123456

julia> big"7891.5"
7891.5

julia> big"_"
ERROR: ArgumentError: invalid number format _ for BigInt or BigFloat
[...]
```

!!! 경고     [`BigFloat`](@ref) 값을 구성하기 위해 `@big_str`를 사용하는 것은 순수하게 예상되는 동작을 초래하지 않을 수 있습니다: 매크로인 `@big_str`는 *로드 시점*에 설정된 전역 정밀도 ([`setprecision`](@ref)) 및 반올림 모드 ([`setrounding`](@ref)) 설정을 따릅니다. 따라서 `() -> precision(big"0.3")`와 같은 함수는 함수가 정의될 때의 정밀도 값에 따라 달라지는 상수를 반환하며, **함수가 호출될 때의** 정밀도에 따라 달라지지 않습니다.
