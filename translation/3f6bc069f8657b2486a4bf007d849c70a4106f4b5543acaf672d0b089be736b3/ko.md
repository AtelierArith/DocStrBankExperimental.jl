```
repr(x; context=nothing)
```

어떤 값으로부터 문자열을 생성하려면 [`show`](@ref) 함수를 사용하세요. `repr`에 메서드를 추가하지 말고 대신 `show` 메서드를 정의해야 합니다.

선택적 키워드 인수 `context`는 `:key=>value` 쌍, `:key=>value` 쌍의 튜플, 또는 `show`에 전달되는 I/O 스트림에 사용되는 속성을 가진 `IO` 또는 [`IOContext`](@ref) 객체로 설정할 수 있습니다.

`repr(x)`는 일반적으로 `x`의 값이 Julia에서 입력되는 방식과 유사합니다. 또한 [`repr(MIME("text/plain"), x)`](@ref)를 참조하여 `x`의 "예쁘게 출력된" 버전을 반환할 수 있으며, 이는 `x`의 REPL 표시와 동등합니다.

!!! compat "Julia 1.7"
    키워드 `context`에 튜플을 전달하려면 Julia 1.7 이상이 필요합니다.


# 예제

```jldoctest
julia> repr(1)
"1"

julia> repr(zeros(3))
"[0.0, 0.0, 0.0]"

julia> repr(big(1/3))
"0.333333333333333314829616256247390992939472198486328125"

julia> repr(big(1/3), context=:compact => true)
"0.333333"
```
