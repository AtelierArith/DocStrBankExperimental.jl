```
SpinLock()
```

创建一个非重入的测试-测试-设置自旋锁。递归使用将导致死锁。这种锁应该仅在执行时间很短且不阻塞的代码周围使用（例如，执行 I/O）。一般来说，应该使用 [`ReentrantLock`](@ref) 代替。

每个 [`lock`](@ref) 必须与一个 [`unlock`](@ref) 匹配。如果 [`!islocked(lck::SpinLock)`](@ref islocked) 为真，则 [`trylock(lck)`](@ref trylock) 成功，除非有其他任务试图“同时”持有锁。

测试-测试-设置自旋锁在大约 30 个竞争线程之前是最快的。如果竞争超过这个数量，则应该考虑不同的同步方法。
