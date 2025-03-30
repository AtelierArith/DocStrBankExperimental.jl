```
isdigit(c::AbstractChar) -> Bool
```

문자가 10진수 숫자(0-9)인지 여부를 테스트합니다.

참고: [`isletter`](@ref).

# 예제

```jldoctest
julia> isdigit('❤')
false

julia> isdigit('9')
true

julia> isdigit('α')
false
```
