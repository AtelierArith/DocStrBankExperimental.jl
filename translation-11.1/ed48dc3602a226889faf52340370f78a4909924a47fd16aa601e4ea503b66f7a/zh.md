```
floorceil(dt::TimeType, p::Period) -> (TimeType, TimeType)
```

同时返回 `Date` 或 `DateTime` 在分辨率 `p` 下的 `floor` 和 `ceil`。比单独调用 `floor` 和 `ceil` 更高效。
