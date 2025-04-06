```
MultiSelectConfig(; charset=:ascii, checked::String, unchecked::String, kwargs...)
```

여러 선택 메뉴의 동작을 키워드 인수를 통해 구성합니다:

  * `checked`는 옵션이 선택되었을 때 출력할 문자열입니다. 기본값은 `charset`에 따라 "[X]" 또는 "✓"입니다.
  * `unchecked`는 옵션이 선택되지 않았을 때 출력할 문자열입니다. 기본값은 `charset`에 따라 "[ ]" 또는 "⬚"입니다.

모든 다른 키워드 인수는 [`TerminalMenus.Config`](@ref)에서 설명된 대로입니다. `checked`와 `unchecked`는 자동으로 출력되지 않으며, `writeline` 메서드에서 출력해야 합니다.

!!! compat "Julia 1.6"
    `MultiSelectConfig`는 Julia 1.6부터 사용할 수 있습니다. 이전 버전에서는 전역 `CONFIG`를 사용하세요.

