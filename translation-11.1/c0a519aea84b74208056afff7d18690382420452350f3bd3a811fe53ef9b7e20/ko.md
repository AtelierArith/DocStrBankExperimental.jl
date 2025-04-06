```
Config(; scroll_wrap=false, ctrl_c_interrupt=true, charset=:ascii, cursor::Char, up_arrow::Char, down_arrow::Char)
```

키워드 인수를 통해 선택 메뉴의 동작을 구성합니다:

  * `scroll_wrap`, `true`인 경우, 메뉴가 첫 번째 항목 위나 마지막 항목 아래로 스크롤할 때 감싸도록 합니다.
  * `ctrl_c_interrupt`, `true`인 경우, 사용자가 메뉴 선택 중 Ctrl-C를 누르면 `InterruptException`을 발생시킵니다. `false`인 경우, [`TerminalMenus.request`](@ref)는 [`TerminalMenus.selected`](@ref)에서 기본 결과를 반환합니다.
  * `charset`은 `cursor`, `up_arrow`, `down_arrow`의 기본 값에 영향을 미치며, `:ascii` 또는 `:unicode`일 수 있습니다.
  * `cursor`는 "Enter"를 눌러 선택할 옵션을 나타내기 위해 인쇄되는 문자입니다. 기본값은 `charset`에 따라 '>' 또는 '→'입니다.
  * `up_arrow`는 표시가 첫 번째 항목을 포함하지 않을 때 인쇄되는 문자입니다. 기본값은 `charset`에 따라 '^' 또는 '↑'입니다.
  * `down_arrow`는 표시가 마지막 항목을 포함하지 않을 때 인쇄되는 문자입니다. 기본값은 `charset`에 따라 'v' 또는 '↓'입니다.

`ConfiguredMenu`의 하위 유형은 필요에 따라 `cursor`, `up_arrow`, `down_arrow`를 자동으로 인쇄하며, 귀하의 `writeline` 메서드는 이를 인쇄하지 않아야 합니다.

!!! compat "Julia 1.6"
    `Config`는 Julia 1.6부터 사용할 수 있습니다. 이전 버전에서는 전역 `CONFIG`를 사용하십시오.

