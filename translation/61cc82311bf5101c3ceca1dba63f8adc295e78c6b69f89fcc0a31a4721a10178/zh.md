```
Threads.@threads [schedule] for ... end
```

一个宏，用于并行执行 `for` 循环。迭代空间被分配给粗粒度的任务。此策略可以通过 `schedule` 参数指定。循环的执行会等待所有迭代的评估。

另请参见: [`@spawn`](@ref Threads.@spawn) 和 [`Distributed`](@ref man-distributed) 中的 `pmap`。

# 扩展帮助

## 语义

除非调度选项指定了更强的保证，否则由 `@threads` 宏执行的循环具有以下语义。

`@threads` 宏以未指定的顺序和潜在的并发方式执行循环体。它不指定任务和工作线程的确切分配。每次执行的分配可能不同。循环体代码（包括从中递归调用的任何代码）不得对迭代分配给任务或执行它们的工作线程的分布做出任何假设。每次迭代的循环体必须能够独立于其他迭代向前推进，并且不受数据竞争的影响。因此，跨迭代的无效同步可能导致死锁，而未同步的内存访问可能导致未定义的行为。

例如，上述条件意味着：

  * 在一个迭代中获取的锁 *必须* 在同一迭代中释放。
  * 使用阻塞原语如 `Channel` 在迭代之间进行通信是不正确的。
  * 仅写入在迭代之间不共享的位置（除非使用锁或原子操作）。
  * 除非使用 `:static` 调度，否则 [`threadid()`](@ref Threads.threadid) 的值可能在单个迭代内发生变化。请参见 [`Task Migration`](@ref man-task-migration)。

## 调度器

如果没有调度器参数，则确切的调度是未指定的，并且在 Julia 版本之间有所不同。目前，当未指定调度器时，使用 `:dynamic`。

!!! compat "Julia 1.5"
    从 Julia 1.5 开始，`schedule` 参数可用。


### `:dynamic`（默认）

`:dynamic` 调度器动态地将迭代分配给可用的工作线程。当前实现假设每个迭代的工作负载是均匀的。然而，这一假设在未来可能会被移除。

此调度选项仅仅是对底层执行机制的提示。然而，可以预期一些属性。`:dynamic` 调度器使用的 `Task` 数量受可用工作线程数量的一个小常数倍的限制（[`Threads.threadpoolsize()`](@ref)）。每个任务处理迭代空间的连续区域。因此，`@threads :dynamic for x in xs; f(x); end` 通常比 `@sync for x in xs; @spawn f(x); end` 更高效，前提是 `length(xs)` 显著大于工作线程的数量，并且 `f(x)` 的运行时间相对小于生成和同步任务的成本（通常小于 10 微秒）。

!!! compat "Julia 1.8"
    从 Julia 1.8 开始，`schedule` 参数的 `:dynamic` 选项可用且为默认值。


### `:greedy`

`:greedy` 调度器最多生成 [`Threads.threadpoolsize()`](@ref) 个任务，每个任务贪婪地处理生成的给定迭代值。只要一个任务完成其工作，它就会从迭代器中获取下一个值。任何单个任务完成的工作不一定是来自迭代器的连续值。给定的迭代器可能会无限生成值，只需要迭代器接口（不需要索引）。

如果单个迭代的工作负载不均匀/有较大差异，这个调度选项通常是一个不错的选择。

!!! compat "Julia 1.11"
    从 Julia 1.11 开始，`schedule` 参数的 `:greedy` 选项可用。


### `:static`

`:static` 调度器为每个线程创建一个任务，并在它们之间均匀分配迭代，将每个任务专门分配给每个线程。特别地，[`threadid()`](@ref Threads.threadid) 的值在一个迭代内是恒定的。如果在另一个 `@threads` 循环内部或从线程 1 以外的线程使用，则指定 `:static` 是错误的。

!!! note
    `:static` 调度的存在是为了支持在 Julia 1.3 之前编写的代码的过渡。在新编写的库函数中，不鼓励使用 `:static` 调度，因为使用此选项的函数不能从任意工作线程调用。


## 示例

为了说明不同的调度策略，考虑以下包含非让步定时循环的函数 `busywait`，该循环运行给定的秒数。

```julia-repl
julia> function busywait(seconds)
            tstart = time_ns()
            while (time_ns() - tstart) / 1e9 < seconds
            end
        end

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :static for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
6.003001 seconds (16.33 k allocations: 899.255 KiB, 0.25% compilation time)

julia> @time begin
            Threads.@spawn busywait(5)
            Threads.@threads :dynamic for i in 1:Threads.threadpoolsize()
                busywait(1)
            end
        end
2.012056 seconds (16.05 k allocations: 883.919 KiB, 0.66% compilation time)
```

`:dynamic` 示例耗时 2 秒，因为一个未占用的线程能够运行两个 1 秒的迭代以完成 for 循环。
