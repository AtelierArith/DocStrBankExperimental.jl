```
floorceil(x::Period, precision::T) where T <: Union{TimePeriod, Week, Day} -> (T, T)
```

同时返回在分辨率 `p` 下的 `Period` 的 `floor` 和 `ceil`。比单独调用 `floor` 和 `ceil` 更高效。
