# [Multi-Threading](@id man-multithreading)

访问这个 [blog post](https://julialang.org/blog/2019/07/multithreading/) 以获取 Julia 多线程特性的演示。

## Starting Julia with multiple threads

默认情况下，Julia 启动时使用单个执行线程。可以通过使用命令 [`Threads.nthreads()`](@ref) 来验证这一点：

```jldoctest
julia> Threads.nthreads()
1
```

执行线程的数量可以通过使用 `-t`/`--threads` 命令行参数或使用 [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) 环境变量来控制。当两者都被指定时，`-t`/`--threads` 优先。

线程的数量可以指定为整数（`--threads=4`）或为 `auto`（`--threads=auto`），其中 `auto` 尝试推断出一个有用的默认线程数量（有关更多详细信息，请参见 [Command-line Options](@ref command-line-interface)）。

!!! compat "Julia 1.5"
    `-t`/`--threads` 命令行参数至少需要 Julia 1.5。在旧版本中，您必须使用环境变量。


!!! compat "Julia 1.7"
    使用 `auto` 作为环境变量 [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) 的值至少需要 Julia 1.7。在旧版本中，此值将被忽略。


让我们用 4 个线程启动 Julia：

```bash
$ julia --threads 4
```

让我们确认我们有4个线程可用。

```julia-repl
julia> Threads.nthreads()
4
```

但我们目前在主线程上。为了检查，我们使用函数 [`Threads.threadid`](@ref)

```jldoctest
julia> Threads.threadid()
1
```

!!! note
    如果您更喜欢使用环境变量，可以在 Bash（Linux/macOS）中按如下方式设置：

    ```bash
    export JULIA_NUM_THREADS=4
    ```

    C shell 在 Linux/macOS 上，CMD 在 Windows 上：

    ```bash
    set JULIA_NUM_THREADS=4
    ```

    在Windows上使用Powershell：

    ```powershell
    $env:JULIA_NUM_THREADS=4
    ```

    请注意，这必须在启动 Julia 之前完成。


!!! note
    指定的线程数 `-t`/`--threads` 会传递给使用 `-p`/`--procs` 或 `--machine-file` 命令行选项生成的工作进程。例如，`julia -p2 -t2` 会生成 1 个主进程和 2 个工作进程，所有三个进程都启用了 2 个线程。要对工作线程进行更细粒度的控制，请使用 [`addprocs`](@ref) 并将 `-t`/`--threads` 作为 `exeflags` 传递。


### Multiple GC Threads

垃圾收集器（GC）可以使用多个线程。使用的线程数量是计算工作线程数量的一半，或者通过 `--gcthreads` 命令行参数配置，或者通过使用环境变量 [`JULIA_NUM_GC_THREADS`](@ref JULIA_NUM_GC_THREADS) 配置。

!!! compat "Julia 1.10"
    `--gcthreads` 命令行参数至少需要 Julia 1.10。


## [Threadpools](@id man-threadpools)

当程序的线程忙于处理许多任务时，任务可能会经历延迟，这可能会对程序的响应能力和交互性产生负面影响。为了解决这个问题，您可以在您 [`Threads.@spawn`](@ref) 时指定一个任务是交互式的：

```julia
using Base.Threads
@spawn :interactive f()
```

交互式任务应避免执行高延迟操作，如果它们是长时间任务，应频繁让出控制权。

Julia 可以启动一个或多个线程，以保留用于运行交互式任务：

```bash
$ julia --threads 3,1
```

环境变量 [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) 也可以以类似的方式使用：

```bash
export JULIA_NUM_THREADS=3,1
```

这会在 `:default` 线程池中启动 3 个线程，在 `:interactive` 线程池中启动 1 个线程：

```julia-repl
julia> using Base.Threads

julia> nthreadpools()
2

julia> threadpool() # the main thread is in the interactive thread pool
:interactive

julia> nthreads(:default)
3

julia> nthreads(:interactive)
1

julia> nthreads()
3
```

!!! note
    `nthreads` 的零参数版本返回默认池中的线程数量。


!!! note
    根据Julia是否以交互线程启动，主线程要么在默认线程池中，要么在交互线程池中。


任一或两个数字都可以用单词 `auto` 替换，这会导致 Julia 选择一个合理的默认值。

## The `@threads` Macro

让我们使用本地线程来做一个简单的例子。让我们创建一个零的数组：

```jldoctest
julia> a = zeros(10)
10-element Vector{Float64}:
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
 0.0
```

让我们使用 4 个线程同时操作这个数组。我们将让每个线程将其线程 ID 写入每个位置。

Julia 支持使用 [`Threads.@threads`](@ref) 宏的并行循环。该宏附加在 `for` 循环前，以指示 Julia 该循环是一个多线程区域：

```julia-repl
julia> Threads.@threads for i = 1:10
           a[i] = Threads.threadid()
       end
```

迭代空间在线程之间进行分割，之后每个线程将其线程 ID 写入分配给它的位置：

```julia-repl
julia> a
10-element Vector{Float64}:
 1.0
 1.0
 1.0
 2.0
 2.0
 2.0
 3.0
 3.0
 4.0
 4.0
```

请注意，[`Threads.@threads`](@ref) 没有像 [`@distributed`](@ref) 那样的可选缩减参数。

### Using `@threads` without data-races

数据竞争的概念在 ["Communication and data races between threads"](@ref man-communication-and-data-races) 中进行了详细阐述。现在只需知道，数据竞争可能导致不正确的结果和危险的错误。

假设我们想要将下面的函数 `sum_single` 进行多线程处理。

```julia-repl
julia> function sum_single(a)
           s = 0
           for i in a
               s += i
           end
           s
       end
sum_single (generic function with 1 method)

julia> sum_single(1:1_000_000)
500000500000
```

简单地添加 `@threads` 会导致数据竞争，因为多个线程同时读取和写入 `s`。

```julia-repl
julia> function sum_multi_bad(a)
           s = 0
           Threads.@threads for i in a
               s += i
           end
           s
       end
sum_multi_bad (generic function with 1 method)

julia> sum_multi_bad(1:1_000_000)
70140554652
```

请注意，结果不是 `500000500000`，如它应该是的那样，并且在每次评估中很可能会改变。

为了解决这个问题，可以使用特定于任务的缓冲区将总和分段为无竞争的块。这里 `sum_single` 被重用，并且有其自己的内部缓冲区 `s`。输入向量 `a` 被分成 `nthreads()` 个块以进行并行处理。然后，我们使用 `Threads.@spawn` 创建任务，分别对每个块进行求和。最后，我们再次使用 `sum_single` 对每个任务的结果进行求和：

```julia-repl
julia> function sum_multi_good(a)
           chunks = Iterators.partition(a, length(a) ÷ Threads.nthreads())
           tasks = map(chunks) do chunk
               Threads.@spawn sum_single(chunk)
           end
           chunk_sums = fetch.(tasks)
           return sum_single(chunk_sums)
       end
sum_multi_good (generic function with 1 method)

julia> sum_multi_good(1:1_000_000)
500000500000
```

!!! note
    缓冲区不应基于 `threadid()` 进行管理，即 `buffers = zeros(Threads.nthreads())`，因为并发任务可能会让出控制权，这意味着多个并发任务可能在给定线程上使用相同的缓冲区，从而引入数据竞争的风险。此外，当可用线程超过一个时，任务可能会在让出点更改线程，这被称为 [task migration](@ref man-task-migration)。


另一个选项是对跨任务/线程共享的变量使用原子操作，这可能会根据操作的特性更具性能优势。

## [Communication and data-races between threads](@id man-communication-and-data-races)

尽管 Julia 的线程可以通过共享内存进行通信，但编写正确且无数据竞争的多线程代码 notoriously 困难。Julia 的 [`Channel`](@ref) 是线程安全的，可以安全地用于通信。下面还有部分内容解释如何使用 [locks](@ref man-using-locks) 和 [atomics](@ref man-atomic-operations) 来避免数据竞争。

### Data-race freedom

您完全有责任确保您的程序没有数据竞争，如果您不遵守该要求，则无法假定此处承诺的任何内容。观察到的结果可能非常不直观。

如果引入数据竞争，Julia 就不是内存安全的。**如果另一个线程可能会写入数据，请非常小心地读取 *任何* 数据，因为这可能导致段错误或更糟的情况**。以下是从不同线程访问全局变量的几种不安全方式：

```julia
Thread 1:
global b = false
global a = rand()
global b = true

Thread 2:
while !b; end
bad_read1(a) # it is NOT safe to access `a` here!

Thread 3:
while !@isdefined(a); end
bad_read2(a) # it is NOT safe to access `a` here
```

### [Using locks to avoid data-races](@id man-using-locks)

一个重要的工具，用于避免数据竞争，从而编写线程安全的代码，是“锁”的概念。锁可以被锁定和解锁。如果一个线程锁定了一个锁，并且没有解锁，则称该线程“持有”该锁。如果只有一个锁，并且我们编写的代码需要持有该锁才能访问某些数据，我们可以确保多个线程永远不会同时访问相同的数据。请注意，锁与变量之间的链接是由程序员而不是程序建立的。

例如，我们可以创建一个锁 `my_lock`，并在我们修改变量 `my_variable` 时锁定它。这可以通过 `@lock` 宏最简单地完成：

```julia-repl
julia> my_lock = ReentrantLock();

julia> my_variable = [1, 2, 3];

julia> @lock my_lock my_variable[1] = 100
100
```

通过在另一个线程上使用相同的锁和变量的类似模式，这些操作就不会出现数据竞争。

我们可以通过 `lock` 的函数版本以以下两种方式执行上述操作：

```julia-repl
julia> lock(my_lock) do
           my_variable[1] = 100
       end
100

julia> begin
           lock(my_lock)
           try
               my_variable[1] = 100
           finally
               unlock(my_lock)
           end
       end
100
```

所有三个选项都是等效的。请注意，最终版本需要一个显式的 `try` 块，以确保锁始终被解锁，而前两个版本则在内部处理此问题。在更改其他线程访问的数据（例如分配给全局或闭包变量）时，始终应使用上述锁模式。未能这样做可能会导致不可预见的严重后果。

### [Atomic Operations](@id man-atomic-operations)

Julia 支持以 *原子* 方式访问和修改值，即以线程安全的方式避免 [race conditions](https://en.wikipedia.org/wiki/Race_condition)。一个值（必须是原始类型）可以被包装为 [`Threads.Atomic`](@ref) 以指示它必须以这种方式访问。这里我们可以看到一个例子：

```julia-repl
julia> i = Threads.Atomic{Int}(0);

julia> ids = zeros(4);

julia> old_is = zeros(4);

julia> Threads.@threads for id in 1:4
           old_is[id] = Threads.atomic_add!(i, id)
           ids[id] = id
       end

julia> old_is
4-element Vector{Float64}:
 0.0
 1.0
 7.0
 3.0

julia> i[]
 10

julia> ids
4-element Vector{Float64}:
 1.0
 2.0
 3.0
 4.0
```

如果我们尝试在没有原子标签的情况下进行加法运算，我们可能会因为竞争条件而得到错误的答案。以下是如果我们不避免竞争条件会发生的情况的示例：

```julia-repl
julia> using Base.Threads

julia> Threads.nthreads()
4

julia> acc = Ref(0)
Base.RefValue{Int64}(0)

julia> @threads for i in 1:1000
          acc[] += 1
       end

julia> acc[]
926

julia> acc = Atomic{Int64}(0)
Atomic{Int64}(0)

julia> @threads for i in 1:1000
          atomic_add!(acc, 1)
       end

julia> acc[]
1000
```

#### [Per-field atomics](@id man-atomics)

我们还可以使用原子操作在更细粒度的层面上，使用 [`@atomic`](@ref Base.@atomic)、[`@atomicswap`](@ref Base.@atomicswap)、[`@atomicreplace`](@ref Base.@atomicreplace) 宏和 [`@atomiconce`](@ref Base.@atomiconce) 宏。

内存模型的具体细节和设计的其他细节写在 [Julia Atomics Manifesto](https://gist.github.com/vtjnash/11b0031f2e2a66c9c24d33e810b34ec0) 中，稍后将正式发布。

在结构体声明中，任何字段都可以用 `@atomic` 装饰，然后任何写入也必须标记为 `@atomic`，并且必须使用定义的原子顺序之一（`:monotonic`、`:acquire`、`:release`、`:acquire_release` 或 `:sequentially_consistent`）。对原子字段的任何读取也可以带有原子顺序约束的注解，或者如果未指定，则将使用单调（放宽）顺序进行。

!!! compat "Julia 1.7"
    每个字段的原子操作至少需要 Julia 1.7。


## Side effects and mutable function arguments

在使用多线程时，我们必须小心使用那些不是 [pure](https://en.wikipedia.org/wiki/Pure_function) 的函数，因为我们可能会得到错误的答案。例如，按照约定，具有 [name ending with `!`](@ref bang-convention) 的函数会修改它们的参数，因此不是纯函数。

## @threadcall

外部库，例如通过 [`ccall`](@ref) 调用的库，为 Julia 的基于任务的 I/O 机制带来了问题。如果一个 C 库执行了阻塞操作，这将阻止 Julia 调度器执行任何其他任务，直到调用返回。（例外情况是调用自定义 C 代码的情况，这些代码回调到 Julia，可能会让出控制权，或者调用 `jl_yield()` 的 C 代码，这是 [`yield`](@ref) 的 C 等价物。）

[`@threadcall`](@ref) 宏提供了一种在这种情况下避免执行停滞的方法。它在一个单独的线程中调度一个 C 函数执行。为此使用了一个默认大小为 4 的线程池。线程池的大小通过环境变量 `UV_THREADPOOL_SIZE` 控制。在等待空闲线程期间，以及一旦线程可用时的函数执行，请求任务（在主 Julia 事件循环中）会让出给其他任务。请注意，`@threadcall` 在执行完成之前不会返回。因此，从用户的角度来看，它是一个像其他 Julia API 一样的阻塞调用。

被调用的函数不应回调到 Julia，因为这会导致段错误。

`@threadcall` 可能会在未来的 Julia 版本中被移除或更改。

## Caveats

此时，Julia 运行时和标准库中的大多数操作可以以线程安全的方式使用，前提是用户代码没有数据竞争。然而，在某些领域，线程支持的稳定工作仍在进行中。多线程编程有许多固有的困难，如果使用线程的程序表现出异常或不良行为（例如崩溃或神秘结果），通常应该首先怀疑线程之间的交互。

在使用 Julia 中的线程时，有一些特定的限制和警告需要注意：

  * 基本集合类型在多个线程同时使用时需要手动锁定，尤其是当至少有一个线程修改集合时（常见的例子包括对数组的 `push!` 操作，或向 `Dict` 中插入项目）。
  * [`@spawn`](@ref Threads.@spawn) 使用的调度是非确定性的，不应依赖。
  * 计算密集型、非内存分配的任务可能会阻止其他分配内存的线程运行垃圾回收。在这些情况下，可能需要插入手动调用 `GC.safepoint()` 以允许垃圾回收运行。这个限制将在未来被移除。
  * 避免并行运行顶级操作，例如 `include` 或 `eval` 类型、方法和模块定义。
  * Be aware that finalizers registered by a library may break if threads are enabled. This may require some transitional work across the ecosystem before threading can be widely adopted with confidence. See the section on [the safe use of finalizers](@ref man-finalizers) for further details.

## [Task Migration](@id man-task-migration)

在某个线程上开始运行任务后，如果任务让出控制权，它可能会转移到另一个线程。

这样的任务可能是以 [`@spawn`](@ref Threads.@spawn) 或 [`@threads`](@ref Threads.@threads) 开始的，尽管 `@threads` 的 `:static` 调度选项确实会冻结线程 ID。

这意味着在大多数情况下 [`threadid()`](@ref Threads.threadid) 不应被视为任务中的常量，因此不应用于索引缓冲区或有状态对象的向量。

!!! compat "Julia 1.7"
    任务迁移是在 Julia 1.7 中引入的。在此之前，任务总是保持在它们启动时所在的同一线程上。


## [Safe use of Finalizers](@id man-finalizers)

因为终结器可以中断任何代码，所以它们在与任何全局状态交互时必须非常小心。不幸的是，使用终结器的主要原因是更新全局状态（纯函数作为终结器通常是相当无意义的）。这使我们陷入了一点困境。处理这个问题有几种方法：

1. 当单线程时，代码可以调用内部的 `jl_gc_enable_finalizers` C 函数，以防止在关键区域内调度终结器。内部，这在某些函数（例如我们的 C 锁）中使用，以防止在执行某些操作（增量包加载、代码生成等）时发生递归。锁和此标志的组合可以用于使终结器安全。
2. 第二种策略是Base在几个地方采用的，即明确延迟最终处理器，直到它能够非递归地获取其锁。以下示例演示了如何将此策略应用于`Distributed.finalize_ref`：

    ```julia
    function finalize_ref(r::AbstractRemoteRef)
        if r.where > 0 # Check if the finalizer is already run
            if islocked(client_refs) || !trylock(client_refs)
                # delay finalizer for later if we aren't free to acquire the lock
                finalizer(finalize_ref, r)
                return nothing
            end
            try # `lock` should always be followed by `try`
                if r.where > 0 # Must check again here
                    # Do actual cleanup here
                    r.where = 0
                end
            finally
                unlock(client_refs)
            end
        end
        nothing
    end
    ```
3. 一个相关的第三种策略是使用无收益队列。我们目前在 Base 中没有实现无锁队列，但 `Base.IntrusiveLinkedListSynchronized{T}` 是合适的。这通常是处理事件循环代码的一个好策略。例如，`Gtk.jl` 就采用了这种策略来管理生命周期引用计数。在这种方法中，我们不在 `finalizer` 内部进行任何显式工作，而是将其添加到一个队列中，以便在更安全的时间运行。事实上，Julia 的任务调度器已经使用了这一点，因此将 finalizer 定义为 `x -> @spawn do_cleanup(x)` 是这种方法的一个例子。然而，请注意，这并不控制 `do_cleanup` 运行在哪个线程上，因此 `do_cleanup` 仍然需要获取一个锁。如果你实现自己的队列，这一点就不需要成立，因为你可以明确地只从你的线程中清空该队列。
