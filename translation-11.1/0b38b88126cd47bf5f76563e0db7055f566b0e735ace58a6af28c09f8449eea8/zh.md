```
AbstractWorkerPool
```

工人池的超类型，例如 [`WorkerPool`](@ref) 和 [`CachingPool`](@ref)。`AbstractWorkerPool` 应该实现：

  * [`push!`](@ref) - 将一个新工人添加到整体池中（可用 + 忙碌）
  * [`put!`](@ref) - 将一个工人放回可用池中
  * [`take!`](@ref) - 从可用池中取出一个工人（用于远程函数执行）
  * [`length`](@ref) - 整体池中可用工人的数量
  * [`isready`](@ref) - 如果对池的 `take!` 操作会阻塞，则返回 false，否则返回 true

上述的默认实现（在 `AbstractWorkerPool` 上）需要字段

  * `channel::Channel{Int}`
  * `workers::Set{Int}`

其中 `channel` 包含空闲工人的 pid，`workers` 是与此池关联的所有工人的集合。
