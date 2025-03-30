```
SamplerSimple(x, data)
```

创建一个采样器，包装给定的值 `x` 和 `data`。该采样器的 `eltype` 等于 `eltype(x)`。

推荐的使用案例是从具有预计算数据的值中进行采样。
