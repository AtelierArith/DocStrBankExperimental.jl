```
findmin!(rval, rind, A) -> (minval, index)
```

找到 `A` 的最小值及其对应的线性索引，沿着 `rval` 和 `rind` 的单例维度，并将结果存储在 `rval` 和 `rind` 中。`NaN` 被视为小于所有其他值，除了 `missing`。

!!! warning
    当任何可变参数与其他参数共享内存时，行为可能会出乎意料。

