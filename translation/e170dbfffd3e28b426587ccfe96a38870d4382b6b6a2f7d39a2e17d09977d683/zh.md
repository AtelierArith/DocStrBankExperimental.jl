```
IOContext
```

`IOContext` 提供了一种在 [`show`](@ref) 方法之间传递输出配置设置的机制。

简而言之，它是一个不可变字典，是 `IO` 的子类。它支持标准字典操作，如 [`getindex`](@ref)，并且也可以用作 I/O 流。
