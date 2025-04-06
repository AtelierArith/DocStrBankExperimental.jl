```
cov(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

计算矩阵 `X` 在维度 `dims` 上的协方差矩阵。如果 `corrected` 为 `true`（默认值），则总和按 `n-1` 进行缩放；如果 `corrected` 为 `false`，则总和按 `n` 进行缩放，其中 `n = size(X, dims)`。
