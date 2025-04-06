```
keypress(m::AbstractMenu, i::UInt32) -> Bool
```

비표준 키 입력 이벤트를 처리합니다. `true`가 반환되면 [`TerminalMenus.request`](@ref)가 종료됩니다. 기본값은 `false`입니다.
