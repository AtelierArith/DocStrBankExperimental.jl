```
findmax!(rval, rind, A) -> (maxval, index)
```

找到 `A` 的最大值及其对应的线性索引，并沿着 `rval` 和 `rind` 的单例维度存储结果。`NaN` 被视为大于所有其他值，除了 `missing`。

!!! warning
    当任何可变参数与其他参数共享内存时，行为可能会出乎意料。

