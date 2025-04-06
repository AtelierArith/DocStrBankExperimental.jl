```
toprev(dt::TimeType, dow::Int; same::Bool=false) -> TimeType
```

将 `dt` 调整为与 `dow` 对应的前一个星期几，其中 `1 = 星期一，2 = 星期二，等等`。设置 `same=true` 允许将当前的 `dt` 视为前一个 `dow`，从而不进行任何调整。
