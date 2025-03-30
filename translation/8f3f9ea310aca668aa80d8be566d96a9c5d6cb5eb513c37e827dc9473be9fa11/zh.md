```
cov(x::AbstractVector, y::AbstractVector; corrected::Bool=true)
```

计算向量 `x` 和 `y` 之间的协方差。如果 `corrected` 为 `true`（默认值），计算 $\frac{1}{n-1}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$，其中 $*$ 表示复共轭，`n = length(x) = length(y)`。如果 `corrected` 为 `false`，计算 $\frac{1}{n}\sum_{i=1}^n (x_i-\bar x) (y_i-\bar y)^*$。
