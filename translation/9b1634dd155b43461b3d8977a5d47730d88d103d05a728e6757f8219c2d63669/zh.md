```
iamax(n, dx, incx)
iamax(dx)
```

找到 `dx` 中绝对值最大的元素的索引。`n` 是 `dx` 的长度，`incx` 是步幅。如果未提供 `n` 和 `incx`，则假定默认值为 `n=length(dx)` 和 `incx=stride1(dx)`。
