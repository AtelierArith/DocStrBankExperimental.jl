```
remote([p::AbstractWorkerPool], f) -> Function
```

返回一个匿名函数，该函数在可用的工作者上执行函数 `f`（如果提供了，则从 [`WorkerPool`](@ref) `p` 中抽取），使用 [`remotecall_fetch`](@ref)。
