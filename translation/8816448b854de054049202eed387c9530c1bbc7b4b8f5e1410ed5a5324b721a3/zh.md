```
randjump(r::MersenneTwister, steps::Integer) -> MersenneTwister
```

创建一个初始化的 `MersenneTwister` 对象，其状态从 `r` 向前移动 `steps` 步（不生成数字）。一个这样的步骤对应于生成两个 `Float64` 数字。对于每个不同的 `steps` 值，内部必须生成一个大的多项式。对于 `steps=big(10)^20`，已经预先计算了一个。
