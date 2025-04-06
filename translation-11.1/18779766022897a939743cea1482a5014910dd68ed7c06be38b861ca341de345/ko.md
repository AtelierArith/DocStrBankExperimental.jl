```
parse(str; raise=true, depwarn=true, filename="none")
```

표현식 문자열을 탐욕스럽게 구문 분석하여 단일 표현식을 반환합니다. 첫 번째 표현식 이후에 추가 문자가 있으면 오류가 발생합니다. `raise`가 `true`(기본값)인 경우 구문 오류가 발생하면 오류가 발생합니다. 그렇지 않으면 `parse`는 평가 시 오류를 발생시키는 표현식을 반환합니다. `depwarn`이 `false`인 경우 사용 중단 경고가 억제됩니다. `filename` 인수는 오류가 발생할 때 진단을 표시하는 데 사용됩니다.

```jldoctest; filter=r"(?<=Expr\(:error).*|(?<=Expr\(:incomplete).*"
julia> Meta.parse("x = 3")
:(x = 3)

julia> Meta.parse("1.0.2")
ERROR: ParseError:
# Error @ none:1:1
1.0.2
└──┘ ── 잘못된 숫자 상수
[...]

julia> Meta.parse("1.0.2"; raise = false)
:($(Expr(:error, "잘못된 숫자 상수 "1.0."")))

julia> Meta.parse("x = ")
:($(Expr(:incomplete, "불완전: 입력의 조기 종료")))
```
