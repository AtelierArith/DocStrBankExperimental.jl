```
cov(x::AbstractVector; corrected::Bool=true)
```

计算向量 `x` 的方差。如果 `corrected` 为 `true`（默认值），则总和按 `n-1` 进行缩放；如果 `corrected` 为 `false`，则总和按 `n` 进行缩放，其中 `n = length(x)`。
