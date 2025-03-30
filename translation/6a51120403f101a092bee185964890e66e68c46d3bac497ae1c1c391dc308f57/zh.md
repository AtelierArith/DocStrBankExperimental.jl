# Instrumenting Julia with DTrace, and bpftrace

DTrace 和 bpftrace 是能够对进程进行轻量级插桩的工具。您可以在进程运行时打开和关闭插桩，并且在插桩关闭时，开销是最小的。

!!! compat "Julia 1.8"
    在 Julia 1.8 中添加了对探针的支持


!!! note
    本文件是从Linux的角度编写的，大部分内容在Mac OS/Darwin和FreeBSD上也适用。


## Enabling support

在Linux上安装包含`dtrace`版本的`systemtap`软件包，并创建一个`Make.user`文件，内容为

```
WITH_DTRACE=1
```

启用 USDT 探针。

### Verifying

```
> readelf -n usr/lib/libjulia-internal.so.1

Displaying notes found in: .note.gnu.build-id
  Owner                Data size  Description
  GNU                  0x00000014 NT_GNU_BUILD_ID (unique build ID bitstring)
    Build ID: 57161002f35548772a87418d2385c284ceb3ead8

Displaying notes found in: .note.stapsdt
  Owner                Data size  Description
  stapsdt              0x00000029 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__begin
    Location: 0x000000000013213e, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cac
    Arguments:
  stapsdt              0x00000032 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__stop_the_world
    Location: 0x0000000000132144, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cae
    Arguments:
  stapsdt              0x00000027 NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__end
    Location: 0x000000000013214a, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb0
    Arguments:
  stapsdt              0x0000002d NT_STAPSDT (SystemTap probe descriptors)
    Provider: julia
    Name: gc__finalizer
    Location: 0x0000000000132150, Base: 0x00000000002bb4da, Semaphore: 0x0000000000346cb2
    Arguments:
```

## Adding probes in libjulia

探针在文件 `src/uprobes.d` 中以 dtraces 格式声明。生成的头文件包含在 `src/julia_internal.h` 中，如果您添加探针，您应该在此处提供一个无操作实现。

头文件将包含一个信号量 `*_ENABLED` 和对探测器的实际调用。如果探测器参数的计算成本较高，您应该首先检查探测器是否启用，然后计算参数并调用探测器。

```c
  if (JL_PROBE_{PROBE}_ENABLED())
    auto expensive_arg = ...;
    JL_PROBE_{PROBE}(expensive_arg);
```

如果您的探针没有参数，建议不包含信号量检查。启用 USDT 探针时，信号量的成本是内存加载，无论探针是否启用。

```c
#define JL_PROBE_GC_BEGIN_ENABLED() __builtin_expect (julia_gc__begin_semaphore, 0)
__extension__ extern unsigned short julia_gc__begin_semaphore __attribute__ ((unused)) __attribute__ ((section (".probes")));
```

而探头本身是一个无操作滑雪板，将被修补到探头处理程序的弹簧床上。

## Available probes

### GC probes

1. `julia:gc__begin`: 垃圾回收开始在一个线程上运行并触发全停顿。
2. `julia:gc__stop_the_world`: 所有线程已到达安全点，GC正在运行。
3. `julia:gc__mark__begin`: 开始标记阶段
4. `julia:gc__mark_end(scanned_bytes, perm_scanned)`: 标记阶段结束
5. `julia:gc__sweep_begin(full)`: 开始清扫
6. `julia:gc__sweep_end`: 清扫阶段完成
7. `julia:gc__end`: 垃圾回收已完成，其他线程继续工作
8. `julia:gc__finalizer`: 初始 GC 线程已完成运行终结器

### Task runtime probes

1. `julia:rt__run__task(task)`: 在当前线程上切换到任务 `task`。
2. `julia:rt__pause__task(task)`: 在当前线程上切换到任务 `task`。
3. `julia:rt__new__task(parent, child)`：任务 `parent` 在当前线程上创建了任务 `child`。
4. `julia:rt__start__task(task)`：任务 `task` 第一次以新堆栈启动。
5. `julia:rt__finish__task(task)`: 任务 `task` 已完成，将不再执行。
6. `julia:rt__start__process__events(task)`: 任务 `task` 开始处理 libuv 事件。
7. `julia:rt__finish__process__events(task)`: 任务 `task` 完成了 libuv 事件的处理。

### Task queue probes

1. `julia:rt__taskq__insert(ptls, task)`: 线程 `ptls` 尝试将 `task` 插入 PARTR 多队列。
2. `julia:rt__taskq__get(ptls, task)`: 线程 `ptls` 从 PARTR 多队列中弹出了 `task`。

### Thread sleep/wake probes

1. `julia:rt__sleep__check__wake(ptls, old_state)`: 线程 (PTLS `ptls`) 正在唤醒，之前处于状态 `old_state`。
2. `julia:rt__sleep__check__wakeup(ptls)`: 线程 (PTLS `ptls`) 自己醒来了。
3. `julia:rt__sleep__check__sleep(ptls)`: 线程 (PTLS `ptls`) 正在尝试休眠。
4. `julia:rt__sleep__check__taskq__wake(ptls)`: 线程 (PTLS `ptls`) 因 PARTR 多队列中的任务而无法进入休眠。
5. `julia:rt__sleep__check__task__wake(ptls)`: 线程 (PTLS `ptls`) 因为 Base 工作队列中的任务而无法进入睡眠状态。
6. `julia:rt__sleep__check__uv__wake(ptls)`: 线程 (PTLS `ptls`) 因 libuv 唤醒而无法进入睡眠状态。

## Probe usage examples

### GC stop-the-world latency

一个示例 `bpftrace` 脚本在 `contrib/gc_stop_the_world_latency.bt` 中给出，它创建了一个所有线程到达安全点的延迟直方图。

运行此 Julia 代码，使用 `julia -t 2`

```
using Base.Threads

fib(x) = x <= 1 ? 1 : fib(x-1) + fib(x-2)

beaver = @spawn begin
    while true
        fib(30)
        # A manual safepoint is necessary since otherwise this loop
        # may never yield to GC.
        GC.safepoint()
    end
end

allocator = @spawn begin
    while true
        zeros(1024)
    end
end

wait(allocator)
```

在第二个终端中

```
> sudo contrib/bpftrace/gc_stop_the_world_latency.bt
Attaching 4 probes...
Tracing Julia GC Stop-The-World Latency... Hit Ctrl-C to end.
^C


@usecs[1743412]:
[4, 8)               971 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@|
[8, 16)              837 |@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@        |
[16, 32)             129 |@@@@@@                                              |
[32, 64)              10 |                                                    |
[64, 128)              1 |                                                    |
```

我们可以看到在执行的 Julia 进程中，停止世界阶段的延迟分布。

### Task spawn monitor

有时知道一个任务何时生成其他任务是很有用的。这可以通过 `rt__new__task` 很容易地看到。探针的第一个参数 `parent` 是正在创建新任务的现有任务。这意味着如果你知道想要监视的任务的地址，你可以轻松地查看该特定任务生成的任务。让我们看看如何做到这一点；首先，让我们启动一个 Julia 会话并获取 PID 和 REPL 的任务地址：

```
> julia
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825

2> current_task()
Task (runnable) @0x00007f524d088010
```

现在我们可以启动 `bpftrace` 并监控 `rt__new__task` 仅针对这个父进程：

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task /arg0==0x00007f524d088010/{ printf("任务: %x\n", arg0); }'`

（请注意，在上面，`arg0` 是第一个参数，`parent`）。

如果我们生成一个单一的任务：

`@async 1+1`

我们看到这个任务被创建：

`任务: 4d088010`

然而，如果我们从那个新生成的任务中派生出一堆任务：

```julia
@async for i in 1:10
   @async 1+1
end
```

我们仍然只看到来自 `bpftrace` 的一个任务：

`任务: 4d088010`

而且这仍然是我们正在监控的相同任务！当然，我们可以移除这个过滤器，以便轻松查看 *所有* 新创建的任务：

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__new__task { printf("任务: %x\n", arg0); }'`

```
Task: 4d088010
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
Task: 4dc4e290
```

我们可以看到我们的根任务，以及新生成的任务作为十个更新任务的父任务。

### Thundering herd detection

任务运行时常常会遭受“雷鸣般的兽群”问题：当一些工作被添加到一个安静的任务运行时，所有线程可能会从它们的沉睡中被唤醒，即使没有足够的工作供每个线程处理。这可能会导致额外的延迟和 CPU 周期，因为所有线程都被唤醒（并同时再次入睡，因为没有找到任何可以执行的工作）。

我们可以很容易地用 `bpftrace` 来说明这个问题。首先，在一个终端中，我们启动 Julia，并使用多个线程（在这个例子中是 6 个），并获取该进程的 PID：

```
> julia -t 6
               _
   _       _ _(_)_     |  Documentation: https://docs.julialang.org
  (_)     | (_) (_)    |
   _ _   _| |_  __ _   |  Type "?" for help, "]?" for Pkg help.
  | | | | | | |/ _` |  |
  | | |_| | | | (_| |  |  Version 1.6.2 (2021-07-14)
 _/ |\__'_|_|_|\__'_|  |  Official https://julialang.org/ release
|__/                   |

1> getpid()
997825
```

在另一个终端中，我们启动 `bpftrace` 监控我们的进程，特别是探测 `rt__sleep__check__wake` 钩子：

`sudo bpftrace -p 997825 -e 'usdt:usr/lib/libjulia-internal.so:julia:rt__sleep__check__wake { printf("线程唤醒! %x\n", arg0); }'`

现在，我们在Julia中创建并执行一个单一任务：

`Threads.@spawn 1+1`

在 `bpftrace` 中，我们看到打印出类似的内容：

```
Thread wake up! 3f926100
Thread wake up! 3ebd5140
Thread wake up! 3f876130
Thread wake up! 3e2711a0
Thread wake up! 3e312190
```

即使我们只生成了一个任务（只有一个线程可以同时处理），我们还是唤醒了所有其他线程！在未来，更智能的任务运行时可能只会唤醒一个线程（或者根本不唤醒；生成任务的线程可以执行这个任务！），我们应该会看到这种行为消失。

### Task Monitor with BPFnative.jl

BPFnative.jl 能够像 `bpftrace` 一样附加到 USDT 探针点。可以使用一个演示来监控任务运行时间、GC 和线程睡眠/唤醒转换 [here](https://github.com/jpsamaroo/BPFnative.jl/blob/master/examples/task-runtime.jl)。

## Notes on using `bpftrace`

一个 bpftrace 格式的示例探针如下：

```
usdt:usr/lib/libjulia-internal.so:julia:gc__begin
{
  @start[pid] = nsecs;
}
```

探针声明采用 `usdt` 类型，然后是库的路径或 PID，提供者名称为 `julia`，探针名称为 `gc__begin`。请注意，我使用的是相对路径指向 `libjulia-internal.so`，但在生产系统上，这可能需要是绝对路径。

## Useful references:

  * [Julia Evans blog on Linux tracing systems](https://jvns.ca/blog/2017/07/05/linux-tracing-systems)
  * [LWN article on USDT and BPF](https://lwn.net/Articles/753601/)
  * [GDB support for probes](https://sourceware.org/gdb/onlinedocs/gdb/Static-Probe-Points.html)
  * [Brendan Gregg – Linux Performance](https://www.brendangregg.com/linuxperf.html)
