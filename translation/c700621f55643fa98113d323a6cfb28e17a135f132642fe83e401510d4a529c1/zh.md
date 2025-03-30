```
ExponentialBackOff(; n=1, first_delay=0.05, max_delay=10.0, factor=5.0, jitter=0.1)
```

一个长度为 `n` 的 [`Float64`](@ref) 迭代器，其元素以 `factor` * (1 ± `jitter`) 的速率指数增长。第一个元素为 `first_delay`，所有元素都被限制在 `max_delay` 之内。
