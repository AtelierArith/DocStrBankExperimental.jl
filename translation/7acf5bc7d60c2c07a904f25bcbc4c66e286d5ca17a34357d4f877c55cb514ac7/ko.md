```
config( <see arguments> )
```

키워드 전용 함수로 전역 메뉴 매개변수를 구성합니다.

# 인수

  * `charset::Symbol=:na`: 사용할 UI 문자(`:ascii` 또는 `:unicode`); 다른 인수에 의해 재정의됨
  * `cursor::Char='>'|'→'`: 커서에 사용할 문자
  * `up_arrow::Char='^'|'↑'`: 위쪽 화살표에 사용할 문자
  * `down_arrow::Char='v'|'↓'`: 아래쪽 화살표에 사용할 문자
  * `checked::String="[X]"|"✓"`: 체크된 항목에 사용할 문자열
  * `unchecked::String="[ ]"|"⬚")`: 체크되지 않은 항목에 사용할 문자열
  * `scroll::Symbol=:nowrap`: `:wrap`인 경우 커서를 위와 아래로 감싸고, `:nowrap`인 경우 커서를 감싸지 않음
  * `supress_output::Bool=false`: 무시된 레거시 인수, 대신 `request`에 `suppress_output`을 키워드 인수로 전달하십시오.
  * `ctrl_c_interrupt::Bool=true`: `false`인 경우 ^C에서 빈 값을 반환하고, `true`인 경우 ^C에서 InterruptException()을 발생시킴

!!! compat "Julia 1.6"
    Julia 1.6부터 `config`는 더 이상 사용되지 않습니다. 대신 `Config` 또는 `MultiSelectConfig`를 사용하십시오.

