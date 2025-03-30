```
lock(f::Function, lock)
```

获取 `lock`，在持有 `lock` 的情况下执行 `f`，并在 `f` 返回时释放 `lock`。如果 `lock` 已被其他任务/线程锁定，则等待其变为可用。

当此函数返回时，`lock` 已被释放，因此调用者不应尝试 `unlock` 它。

另见: [`@lock`](@ref)。

!!! compat "Julia 1.7"
    将 [`Channel`](@ref) 作为第二个参数需要 Julia 1.7 或更高版本。

