```
scal!(n, a, X, incx)
scal!(a, X)
```

用 `a*X` 覆盖数组 `X` 的前 `n` 个元素，步长为 `incx`。返回 `X`。

如果未提供 `n` 和 `incx`，则使用 `length(X)` 和 `stride(X,1)`。
