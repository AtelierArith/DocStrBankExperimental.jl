关于 [`Threads.Condition`](@ref) 的特别说明：

调用者必须持有拥有 `Threads.Condition` 的 [`lock`](@ref)，才能调用此方法。调用任务将被阻塞，直到其他任务唤醒它，通常是通过在同一 `Threads.Condition` 对象上调用 [`notify`](@ref)。在阻塞时，锁将被原子释放（即使它是递归锁定的），并将在返回之前重新获取。
