```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Profile/docs/src/index.md"
```

# [Profiling](@id lib-profiling)

## CPU Profiling

有两种主要的方法来对 Julia 代码进行 CPU 性能分析：

## Via `@profile`

在通过 `@profile` 宏为给定调用启用分析的地方。

```julia-repl
julia> using Profile

julia> @profile foo()

julia> Profile.print()
Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
    ╎147  @Base/client.jl:506; _start()
        ╎ 147  @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...
```

## Triggered During Execution

已经在运行的任务也可以在任何用户触发的时间内进行固定时间段的分析。

要触发分析：

  * MacOS 和 FreeBSD（基于 BSD 的平台）：使用 `ctrl-t` 或向 julia 进程发送 `SIGINFO` 信号，即 `% kill -INFO $julia_pid`
  * Linux：向 julia 进程发送 `SIGUSR1` 信号，即 `% kill -USR1 $julia_pid`
  * Windows：当前不支持。

首先，显示在信号抛出瞬间的单个堆栈跟踪，然后收集1秒的性能分析，接着在下一个让步点（对于没有让步点的代码，例如紧密循环，可能是在任务完成时）显示性能分析报告。

可选地将环境变量 [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@ref JULIA_PROFILE_PEEK_HEAP_SNAPSHOT) 设置为 `1`，以便自动收集 [heap snapshot](@ref Heap-Snapshots)。

```julia-repl
julia> foo()
##== the user sends a trigger while foo is running ==##
load: 2.53  cmd: julia 88903 running 6.16u 0.97s

======================================================================================
Information request received. A stacktrace will print followed by a 1.0 second profile
======================================================================================

signal (29): Information request: 29
__psynch_cvwait at /usr/lib/system/libsystem_kernel.dylib (unknown line)
_pthread_cond_wait at /usr/lib/system/libsystem_pthread.dylib (unknown line)
...

======================================================================
Profile collected. A report will print if the Profile module is loaded
======================================================================

Overhead ╎ [+additional indent] Count File:Line; Function
=========================================================
Thread 1 Task 0x000000011687c010 Total snapshots: 572. Utilization: 100%
   ╎147 @Base/client.jl:506; _start()
       ╎ 147 @Base/client.jl:318; exec_options(opts::Base.JLOptions)
...

Thread 2 Task 0x0000000116960010 Total snapshots: 572. Utilization: 0%
   ╎572 @Base/task.jl:587; task_done_hook(t::Task)
      ╎ 572 @Base/task.jl:879; wait()
...
```

### Customization

剖析的持续时间可以通过 [`Profile.set_peek_duration`](@ref) 进行调整。

配置报告按线程和任务进行细分。将一个无参数函数传递给 `Profile.peek_report[]` 以覆盖此设置。即 `Profile.peek_report[] = () -> Profile.print()` 以移除任何分组。这也可以被外部配置数据消费者覆盖。

## Reference

```@docs
Profile.@profile
```

`Profile` 中的方法未被导出，需要通过例如 `Profile.print()` 的方式调用。

```@docs
Profile.clear
Profile.print
Profile.init
Profile.fetch
Profile.retrieve
Profile.callers
Profile.clear_malloc_data
Profile.get_peek_duration
Profile.set_peek_duration
```

## Memory profiling

```@docs
Profile.Allocs.@profile
```

`Profile.Allocs` 中的方法未被导出，需要通过例如 `Profile.Allocs.fetch()` 的方式调用。

```@docs
Profile.Allocs.clear
Profile.Allocs.print
Profile.Allocs.fetch
Profile.Allocs.start
Profile.Allocs.stop
```

## Heap Snapshots

```@docs
Profile.take_heap_snapshot
```

`Profile` 中的方法未被导出，需要通过例如 `Profile.take_heap_snapshot()` 的方式调用。

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot.heapsnapshot")
```

跟踪和记录堆上的 Julia 对象。这仅记录 Julia 垃圾收集器已知的对象。未被垃圾收集器管理的外部库分配的内存将不会出现在快照中。

为了避免在记录快照时出现内存溢出，我们添加了一个流式选项，将堆快照流式输出到四个文件中，

```julia-repl
julia> using Profile

julia> Profile.take_heap_snapshot("snapshot"; streaming=true)
```

其中“snapshot”是生成文件的前缀路径。

一旦快照文件生成，可以使用以下命令离线组装：

```julia-repl
julia> using Profile

julia> Profile.HeapSnapshot.assemble_snapshot("snapshot", "snapshot.heapsnapshot")
```

生成的堆快照文件可以上传到 Chrome 开发者工具中查看。有关更多信息，请参见 [chrome devtools docs](https://developer.chrome.com/docs/devtools/memory-problems/heap-snapshots/#view_snapshots)。分析 Chromium 堆快照的另一种方法是使用 VS Code 扩展 `ms-vscode.vscode-js-profile-flame`。

Firefox 的堆快照格式不同，目前可能 *无法* 用于查看由 Julia 生成的堆快照。
