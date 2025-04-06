```
toprev(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

`dt`를 `dow`에 해당하는 이전 주의 날로 조정합니다. 여기서 `1 = 월요일, 2 = 화요일, 등`입니다. `same=true`로 설정하면 현재 `dt`를 이전 `dow`로 간주할 수 있어 조정이 발생하지 않습니다.
