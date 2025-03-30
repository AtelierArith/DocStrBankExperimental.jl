```
ReentrantLock()
```

创建一个可重入锁用于同步 [`Task`](@ref)s。相同的任务可以根据需要多次获取锁（这就是名称中“可重入”部分的意思）。每个 [`lock`](@ref) 必须与一个 [`unlock`](@ref) 匹配。

调用 `lock` 还会抑制该线程上终结器的运行，直到相应的 `unlock`。下面所示的标准锁模式的使用应该自然得到支持，但要小心反转尝试/锁定顺序或完全遗漏尝试块（例如，尝试在仍持有锁的情况下返回）：

这提供了锁/解锁调用的获取/释放内存顺序。

```
lock(l)
try
    <atomic work>
finally
    unlock(l)
end
```

如果 [`!islocked(lck::ReentrantLock)`](@ref islocked) 为真，则 [`trylock(lck)`](@ref trylock) 成功，除非有其他任务试图“同时”持有锁。
