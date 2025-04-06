# [Asynchronous Programming](@id man-asynchronous)

当一个程序需要与外部世界互动时，例如通过互联网与另一台机器通信，程序中的操作可能需要以不可预测的顺序发生。假设您的程序需要下载一个文件。我们希望启动下载操作，在等待其完成的同时执行其他操作，然后在文件可用时恢复需要下载文件的代码。这种场景属于异步编程的范畴，有时也称为并发编程（因为在概念上，多个事情是同时发生的）。

为了应对这些场景，Julia 提供了 [`Task`](@ref)（也被称为对称协程、轻量级线程、协作多任务处理或一次性继续）。当一段计算工作（实际上是执行特定函数）被指定为 `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` 时，可以通过切换到另一个 `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` 来中断它。原始的 `4d61726b646f776e2e436f64652822222c20225461736b2229_40726566` 可以在稍后恢复，此时它将从中断的地方继续执行。起初，这可能看起来与函数调用相似。然而，有两个关键的区别。首先，切换任务不使用任何空间，因此可以在不消耗调用栈的情况下进行任意数量的任务切换。其次，任务之间的切换可以以任何顺序发生，而与函数调用不同，后者必须在控制返回到调用函数之前完成执行。

## Basic `Task` operations

您可以将 `Task` 视为一个处理要执行的计算工作单元的句柄。它具有创建-开始-运行-完成的生命周期。通过在要运行的 0 参数函数上调用 `Task` 构造函数，或使用 [`@task`](@ref) 宏来创建任务：

```julia-repl
julia> t = @task begin; sleep(5); println("done"); end
Task (runnable) @0x00007f13a40c0eb0
```

`@task x` 相当于 `Task(()->x)`。

此任务将等待五秒钟，然后打印 `done`。然而，它尚未开始运行。我们可以在准备好时通过调用 [`schedule`](@ref) 来运行它：

```julia-repl
julia> schedule(t);
```

如果你在 REPL 中尝试这个，你会看到 `schedule` 立即返回。这是因为它只是将 `t` 添加到一个内部任务队列中。然后，REPL 将打印下一个提示并等待更多输入。等待键盘输入为其他任务提供了运行的机会，因此在那时 `t` 将开始。`t` 调用 [`sleep`](@ref)，这会设置一个计时器并停止执行。如果其他任务已经被调度，它们可能会在那时运行。五秒后，计时器触发并重新启动 `t`，你将看到 `done` 被打印。`t` 然后完成。

[`wait`](@ref) 函数会阻塞调用任务，直到其他任务完成。因此，例如，如果你输入

```julia-repl
julia> schedule(t); wait(t)
```

而不是仅仅调用 `schedule`，您会看到在下一个输入提示出现之前有五秒的暂停。这是因为 REPL 正在等待 `t` 完成后再继续。

通常希望创建一个任务并立即安排它，因此提供了宏 [`@async`](@ref) 以实现该目的——`@async x` 相当于 `schedule(@task x)`。

## Communicating with Channels

在某些问题中，各个所需工作的部分并没有通过函数调用自然关联；在需要完成的任务中没有明显的“调用者”或“被调用者”。一个例子是生产者-消费者问题，其中一个复杂的过程正在生成值，而另一个复杂的过程正在消费这些值。消费者不能简单地调用生产者函数来获取值，因为生产者可能还有更多的值要生成，因此可能尚未准备好返回。通过任务，生产者和消费者可以根据需要同时运行，必要时相互传递值。

Julia 提供了一种 [`Channel`](@ref) 机制来解决这个问题。`4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` 是一个可等待的先进先出队列，可以有多个任务从中读取和写入。

让我们定义一个生产者任务，通过 [`put!`](@ref) 调用生成值。为了消费值，我们需要安排生产者在一个新任务中运行。可以使用一个特殊的 [`Channel`](@ref) 构造函数，该构造函数接受一个带有 1 个参数的函数作为参数，可以用来运行绑定到通道的任务。然后我们可以从通道对象中重复 [`take!`](@ref) 值：

```jldoctest producer
julia> function producer(c::Channel)
           put!(c, "start")
           for n=1:4
               put!(c, 2n)
           end
           put!(c, "stop")
       end;

julia> chnl = Channel(producer);

julia> take!(chnl)
"start"

julia> take!(chnl)
2

julia> take!(chnl)
4

julia> take!(chnl)
6

julia> take!(chnl)
8

julia> take!(chnl)
"stop"
```

一种理解这种行为的方法是，`producer`能够多次返回。在调用[`put!`](@ref)之间，生产者的执行被挂起，消费者获得控制权。

返回的 [`Channel`](@ref) 可以作为可迭代对象在 `for` 循环中使用，在这种情况下，循环变量会获取所有生成的值。当通道关闭时，循环终止。

```jldoctest producer
julia> for x in Channel(producer)
           println(x)
       end
start
2
4
6
8
stop
```

请注意，我们不需要在生产者中显式关闭通道。这是因为将 [`Channel`](@ref) 绑定到 [`Task`](@ref) 的行为将通道的开放生命周期与绑定任务的生命周期关联起来。当任务终止时，通道对象会自动关闭。多个通道可以绑定到一个任务，反之亦然。

虽然 [`Task`](@ref) 构造函数期望一个无参数的函数，但创建任务绑定通道的 [`Channel`](@ref) 方法期望一个接受单个参数类型为 `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` 的函数。一个常见的模式是生产者被参数化，在这种情况下，需要部分函数应用来创建一个 0 或 1 参数的 [anonymous function](@ref man-anonymous-functions)。

对于 [`Task`](@ref) 对象，可以直接进行此操作或使用便利宏：

```julia
function mytask(myarg)
    ...
end

taskHdl = Task(() -> mytask(7))
# or, equivalently
taskHdl = @task mytask(7)
```

为了协调更高级的工作分配模式，可以将 [`bind`](@ref) 和 [`schedule`](@ref) 与 [`Task`](@ref) 和 [`Channel`](@ref) 构造函数结合使用，以明确将一组通道与一组生产者/消费者任务链接起来。

### More on Channels

一个通道可以被视为一根管道，即它有一个写入端和一个读取端：

  * 多个作者可以通过 [`put!`](@ref) 调用在不同任务中同时写入同一频道。
  * 多个读者可以通过 [`take!`](@ref) 调用在不同任务中并发读取数据。
  * 作为一个例子：

    ```julia
    # Given Channels c1 and c2,
    c1 = Channel(32)
    c2 = Channel(32)

    # and a function `foo` which reads items from c1, processes the item read
    # and writes a result to c2,
    function foo()
        while true
            data = take!(c1)
            [...]               # process data
            put!(c2, result)    # write out result
        end
    end

    # we can schedule `n` instances of `foo` to be active concurrently.
    for _ in 1:n
        errormonitor(@async foo())
    end
    ```
  * 通道是通过 `Channel{T}(sz)` 构造函数创建的。通道只会保存类型为 `T` 的对象。如果未指定类型，则通道可以保存任何类型的对象。`sz` 指的是通道在任何时候可以容纳的最大元素数量。例如，`Channel(32)` 创建了一个可以容纳最多 32 个任何类型对象的通道。`Channel{MyType}(64)` 可以在任何时候容纳最多 64 个 `MyType` 类型的对象。
  * 如果 [`Channel`](@ref) 为空，读者（在 [`take!`](@ref) 调用上）将会阻塞，直到数据可用。
  * 如果 [`Channel`](@ref) 已满，写入者（在 [`put!`](@ref) 调用上）将会阻塞，直到有空间可用。
  * [`isready`](@ref) 测试通道中是否存在任何对象，而 [`wait`](@ref) 则等待对象变得可用。
  * 一个 [`Channel`](@ref) 最初处于开放状态。这意味着可以通过 [`take!`](@ref) 和 [`put!`](@ref) 调用自由地读取和写入。 [`close`](@ref) 关闭一个 `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`。在关闭的 `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566` 上，`4d61726b646f776e2e436f64652822222c2022707574212229_40726566` 将失败。例如：

    ```julia-repl
    julia> c = Channel(2);

    julia> put!(c, 1) # `put!` on an open channel succeeds
    1

    julia> close(c);

    julia> put!(c, 2) # `put!` on a closed channel throws an exception.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```
  * [`take!`](@ref) 和 [`fetch`](@ref)（这会检索但不会移除值）在一个关闭的频道上成功返回任何现有值，直到它被清空。继续上述示例：

    ```julia-repl
    julia> fetch(c) # Any number of `fetch` calls succeed.
    1

    julia> fetch(c)
    1

    julia> take!(c) # The first `take!` removes the value.
    1

    julia> take!(c) # No more data available on a closed channel.
    ERROR: InvalidStateException: Channel is closed.
    Stacktrace:
    [...]
    ```

考虑一个使用通道进行任务间通信的简单示例。我们启动4个任务来处理来自单个`jobs`通道的数据。作业通过一个id（`job_id`）写入通道。在这个模拟中，每个任务读取一个`job_id`，等待随机的时间，然后将`job_id`和模拟时间的元组写回结果通道。最后，所有的`results`都被打印出来。

```julia-repl
julia> const jobs = Channel{Int}(32);

julia> const results = Channel{Tuple}(32);

julia> function do_work()
           for job_id in jobs
               exec_time = rand()
               sleep(exec_time)                # simulates elapsed time doing actual work
                                               # typically performed externally.
               put!(results, (job_id, exec_time))
           end
       end;

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for i in 1:4 # start 4 tasks to process requests in parallel
           errormonitor(@async do_work())
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds")
           global n = n - 1
       end
4 finished in 0.22 seconds
3 finished in 0.45 seconds
1 finished in 0.5 seconds
7 finished in 0.14 seconds
2 finished in 0.78 seconds
5 finished in 0.9 seconds
9 finished in 0.36 seconds
6 finished in 0.87 seconds
8 finished in 0.79 seconds
10 finished in 0.64 seconds
12 finished in 0.5 seconds
11 finished in 0.97 seconds
0.029772311
```

与其使用 `errormonitor(t)`，不如使用 `bind(results, t)`，因为这不仅会记录任何意外的失败，还会强制关闭相关资源并在各处传播异常。

## More task operations

任务操作是建立在一个低级原语上，称为 [`yieldto`](@ref)。`yieldto(task, value)` 会挂起当前任务，切换到指定的 `task`，并使该任务的最后一次 `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` 调用返回指定的 `value`。请注意，`4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` 是使用任务风格控制流所需的唯一操作；我们总是通过切换到不同的任务，而不是调用和返回。这就是为什么这个特性也被称为“对称协程”；每个任务都是使用相同的机制进行切换的。

[`yieldto`](@ref) 是强大的，但大多数任务的使用并不直接调用它。考虑一下这可能的原因。如果你切换离开当前任务，你可能会想在某个时刻切换回去，但知道何时切换回去，以及知道哪个任务负责切换回去，可能需要相当大的协调。例如，[`put!`](@ref) 和 [`take!`](@ref) 是阻塞操作，当在通道的上下文中使用时，保持状态以记住消费者是谁。不需要手动跟踪消费任务是使 `4d61726b646f776e2e436f64652822222c2022707574212229_40726566` 比低级的 `4d61726b646f776e2e436f64652822222c20227969656c64746f2229_40726566` 更易于使用的原因。

除了 [`yieldto`](@ref)，还需要一些其他基本功能来有效地使用任务。

  * [`current_task`](@ref) 获取对当前运行任务的引用。
  * [`istaskdone`](@ref) 查询一个任务是否已退出。
  * [`istaskstarted`](@ref) 查询一个任务是否已经运行。
  * [`task_local_storage`](@ref) 操作特定于当前任务的键值存储。

## Tasks and events

大多数任务切换是由于等待事件（例如 I/O 请求）而发生的，并由包含在 Julia Base 中的调度器执行。调度器维护一个可运行任务的队列，并执行一个事件循环，根据外部事件（例如消息到达）重新启动任务。

The basic function for waiting for an event is [`wait`](@ref). Several objects implement [`wait`](@ref); for example, given a `Process` object, [`wait`](@ref) will wait for it to exit. [`wait`](@ref) is often implicit; for example, a [`wait`](@ref) can happen inside a call to [`read`](@ref) to wait for data to be available.

在所有这些情况下，[`wait`](@ref) 最终操作一个 [`Condition`](@ref) 对象，该对象负责排队和重启任务。当一个任务在 `4d61726b646f776e2e436f64652822222c2022776169742229_40726566` 上调用一个 `4d61726b646f776e2e436f64652822222c2022436f6e646974696f6e2229_40726566` 时，该任务被标记为不可运行，添加到条件的队列中，并切换到调度器。然后，调度器将选择另一个任务来运行，或者阻塞等待外部事件。如果一切顺利，最终事件处理程序将调用 [`notify`](@ref) 在条件上，这会导致等待该条件的任务再次变为可运行。

一个通过调用 [`Task`](@ref) 明确创建的任务最初对调度器来说是未知的。这允许您在需要时使用 [`yieldto`](@ref) 手动管理任务。然而，当这样的任务等待事件时，当事件发生时，它仍然会自动重新启动，正如您所期望的那样。
