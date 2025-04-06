```
isnumeric(c::AbstractChar) -> Bool
```

문자가 숫자인지 여부를 테스트합니다. 문자는 유니코드 일반 범주 번호에 속하는 경우 숫자로 분류됩니다. 즉, 범주 코드가 'N'으로 시작하는 문자입니다.

이 넓은 범주에는 ¾ 및 ௰과 같은 문자가 포함됩니다. 문자가 0과 9 사이의 10진 숫자인지 확인하려면 [`isdigit`](@ref)를 사용하세요.

# 예시

```jldoctest
julia> isnumeric('௰')
true

julia> isnumeric('9')
true

julia> isnumeric('α')
false

julia> isnumeric('❤')
false
```
