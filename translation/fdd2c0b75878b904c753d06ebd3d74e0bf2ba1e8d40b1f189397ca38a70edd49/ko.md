```
request(m::AbstractMenu; cursor=1)
```

메뉴를 표시하고 대화형 모드로 들어갑니다. `cursor`는 초기 커서 위치에 사용되는 항목 번호를 나타냅니다. `cursor`는 `Int` 또는 `RefValue{Int}`일 수 있습니다. 후자는 외부에서 커서 위치를 관찰하고 제어하는 데 유용합니다.

`selected(m)`을 반환합니다.

!!! compat "Julia 1.6"
    `cursor` 인수는 Julia 1.6 이상이 필요합니다.

