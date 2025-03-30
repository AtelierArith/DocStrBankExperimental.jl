```
rmprocs(pids...; waitfor=typemax(Int))
```

移除指定的工作进程。请注意，只有进程 1 可以添加或移除工作进程。

参数 `waitfor` 指定等待工作进程关闭的时间：

  * 如果未指定，`rmprocs` 将等待直到所有请求的 `pids` 被移除。
  * 如果在请求的 `waitfor` 秒之前无法终止所有工作进程，将引发 [`ErrorException`](@ref)。
  * 当 `waitfor` 值为 0 时，调用将立即返回，工作进程将在不同的任务中安排移除。返回调度的 [`Task`](@ref) 对象。用户应在调用任何其他并行调用之前对任务调用 [`wait`](@ref)。

# 示例

```julia-repl
$ julia -p 5

julia> t = rmprocs(2, 3, waitfor=0)
Task (runnable) @0x0000000107c718d0

julia> wait(t)

julia> workers()
3-element Array{Int64,1}:
 4
 5
 6
```
