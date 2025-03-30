```
acquire(f, s::Semaphore)
```

在从信号量 `s` 获取后执行 `f`，并在完成或出错时 `release`。

例如，确保同时只有 2 次 `foo` 调用处于活动状态的 do-block 形式：

```julia
s = Base.Semaphore(2)
@sync for _ in 1:100
    Threads.@spawn begin
        Base.acquire(s) do
            foo()
        end
    end
end
```

!!! compat "Julia 1.8"
    此方法至少需要 Julia 1.8。

