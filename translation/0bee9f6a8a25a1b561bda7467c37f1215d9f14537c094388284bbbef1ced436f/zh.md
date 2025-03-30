```
Threads.Condition([lock])
```

一个线程安全的 [`Base.Condition`](@ref) 版本。

要在 `Threads.Condition` 上调用 [`wait`](@ref) 或 [`notify`](@ref)，您必须首先在其上调用 [`lock`](@ref)。当调用 `wait` 时，锁在阻塞期间会被原子释放，并将在 `wait` 返回之前重新获取。因此，`Threads.Condition` `c` 的惯用用法如下所示：

```
lock(c)
try
    while !thing_we_are_waiting_for
        wait(c)
    end
finally
    unlock(c)
end
```

!!! compat "Julia 1.2"
    此功能至少需要 Julia 1.2。

