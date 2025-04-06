```
partialsort(v, k, by=identity, lt=isless, rev=false)
```

[`partialsort!`](@ref) 的变体，它在部分排序之前复制 `v`，因此返回与 `partialsort!` 相同的结果，但不修改 `v`。
