```
isletter(c::AbstractChar) -> Bool
```

문자가 글자인지 테스트합니다. 문자는 유니코드 일반 범주 Letter에 속하는 경우 글자로 분류됩니다. 즉, 범주 코드가 'L'로 시작하는 문자입니다.

참고: [`isdigit`](@ref).

# 예제

```jldoctest
julia> isletter('❤')
false

julia> isletter('α')
true

julia> isletter('9')
false
```
