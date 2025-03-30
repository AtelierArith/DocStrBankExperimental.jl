```
parse(str, start; greedy=true, raise=true, depwarn=true, filename="none")
```

표현식 문자열을 파싱하고 표현식을 반환합니다(나중에 실행을 위해 eval에 전달될 수 있음). `start`는 파싱을 시작할 첫 번째 문자의 `str`에 대한 코드 유닛 인덱스입니다(모든 문자열 인덱싱과 마찬가지로, 이는 문자 인덱스가 아닙니다). `greedy`가 `true`(기본값)인 경우, `parse`는 가능한 한 많은 입력을 소비하려고 시도합니다. 그렇지 않으면 유효한 표현식을 파싱하는 즉시 중지합니다. 불완전하지만 구문적으로 유효한 표현식은 `Expr(:incomplete, "(error message)")`를 반환합니다. `raise`가 `true`(기본값)인 경우, 불완전한 표현식을 제외한 구문 오류는 오류를 발생시킵니다. `raise`가 `false`인 경우, `parse`는 평가 시 오류를 발생시키는 표현식을 반환합니다. `depwarn`이 `false`인 경우, 사용 중단 경고가 억제됩니다. `filename` 인수는 오류가 발생할 때 진단을 표시하는 데 사용됩니다.

```jldoctest
julia> Meta.parse("(α, β) = 3, 5", 1) # start of string
(:((α, β) = (3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 1, greedy=false)
(:((α, β)), 9)

julia> Meta.parse("(α, β) = 3, 5", 16) # end of string
(nothing, 16)

julia> Meta.parse("(α, β) = 3, 5", 11) # index of 3
(:((3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 11, greedy=false)
(3, 13)
```
