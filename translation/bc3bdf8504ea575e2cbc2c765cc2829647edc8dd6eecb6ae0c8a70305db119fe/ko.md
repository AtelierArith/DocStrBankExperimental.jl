```
writeline(buf::IO, m::AbstractMenu, idx::Int, iscursor::Bool)
```

인덱스 `idx`에 있는 옵션을 `buf`에 씁니다. `iscursor`가 `true`인 경우, 이 항목이 현재 커서 위치에 있음을 나타냅니다(즉, "Enter"를 눌러 선택될 항목).

`m`이 `ConfiguredMenu`인 경우, `TerminalMenus`는 커서 표시기를 출력합니다. 그렇지 않으면 호출자는 그러한 출력을 처리해야 합니다.

!!! compat "Julia 1.6"
    `writeline`은 Julia 1.6 이상이 필요합니다.

    이전 버전의 Julia에서는 `writeLine(buf::IO, m::AbstractMenu, idx, iscursor::Bool)`였으며, `m`은 구성되지 않은 것으로 가정됩니다. 선택 및 커서 표시기는 `TerminalMenus.CONFIG`에서 얻을 수 있습니다.

    이 이전 함수는 모든 Julia 1.x 버전에서 지원되지만 Julia 2.0에서는 제거될 예정입니다.

