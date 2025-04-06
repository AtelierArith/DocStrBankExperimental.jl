# Multi-processing and Distributed Computing

模块 [`Distributed`](@ref man-distributed) 提供了分布式内存并行计算的实现，作为随 Julia 附带的标准库的一部分。

大多数现代计算机拥有多个 CPU，并且可以将几台计算机组合在一起形成集群。利用这些多个 CPU 的强大功能可以更快地完成许多计算。影响性能的两个主要因素是 CPU 本身的速度和它们访问内存的速度。在集群中，显然给定的 CPU 将对同一计算机（节点）内的 RAM 具有最快的访问速度。或许更令人惊讶的是，典型的多核笔记本电脑上也存在类似的问题，这与主内存的速度和 [cache](https://www.akkadia.org/drepper/cpumemory.pdf) 的速度差异有关。因此，一个良好的多处理环境应该允许特定 CPU 对一块内存的“所有权”进行控制。Julia 提供了一个基于消息传递的多处理环境，允许程序在多个进程中同时运行在不同的内存域中。

Julia 的消息传递实现与其他环境（如 MPI[^1]）不同。Julia 中的通信通常是“单边”的，这意味着程序员只需显式管理两个进程操作中的一个。此外，这些操作通常看起来不像“消息发送”和“消息接收”，而更像是对用户函数的调用等更高级的操作。

在Julia中，分布式编程建立在两个原语之上：*远程引用*和*远程调用*。远程引用是一个对象，可以从任何进程使用，以引用存储在特定进程上的对象。远程调用是一个进程请求在另一个（可能是相同的）进程上以某些参数调用某个函数。

远程引用有两种类型：[`Future`](@ref Distributed.Future) 和 [`RemoteChannel`](@ref)。

一个远程调用返回了一个 [`Future`](@ref Distributed.Future) 作为其结果。远程调用会立即返回；发起调用的进程会在远程调用发生的同时继续进行下一个操作。您可以通过调用 [`wait`](@ref) 来等待远程调用完成，并且可以使用 [`fetch`](@ref) 来获取结果的完整值。

另一方面，[`RemoteChannel`](@ref) 是可重写的。例如，多个进程可以通过引用相同的远程 `Channel` 来协调它们的处理。

每个进程都有一个相关的标识符。提供交互式 Julia 提示的进程的 `id` 始终等于 1。默认用于并行操作的进程被称为“工作进程”。当只有一个进程时，进程 1 被视为工作进程。否则，工作进程被视为除进程 1 之外的所有进程。因此，添加 2 个或更多进程是获得并行处理方法（如 [`pmap`](@ref)）好处所必需的。如果您只希望在主进程中做其他事情，而长时间的计算在工作进程上运行，则添加一个进程是有益的。

让我们试试这个。从 `julia -p n` 开始会在本地机器上提供 `n` 个工作进程。通常情况下，`n` 等于机器上 CPU 线程（逻辑核心）的数量是有意义的。请注意，`-p` 参数隐式加载模块 [`Distributed`](@ref man-distributed)。

```julia
$ julia -p 2

julia> r = remotecall(rand, 2, 2, 2)
Future(2, 1, 4, nothing)

julia> s = @spawnat 2 1 .+ fetch(r)
Future(2, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.18526  1.50912
 1.16296  1.60607
```

[`remotecall`](@ref) 的第一个参数是要调用的函数。Julia 中的大多数并行编程不引用特定的进程或可用的进程数量，但 `4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` 被认为是一个低级接口，提供了更细致的控制。`4d61726b646f776e2e436f64652822222c202272656d6f746563616c6c2229_40726566` 的第二个参数是将执行工作的进程的 `id`，其余参数将传递给被调用的函数。

如您所见，在第一行中，我们要求进程 2 构造一个 2x2 的随机矩阵，在第二行中，我们要求它加 1。两个计算的结果可在两个未来值 `r` 和 `s` 中获得。[`@spawnat`](@ref) 宏在由第一个参数指定的进程上评估第二个参数中的表达式。

偶尔你可能希望立即获得一个远程计算的值。这通常发生在你从远程对象读取以获取下一个本地操作所需的数据时。函数 [`remotecall_fetch`](@ref) 存在于此目的。它等同于 `fetch(remotecall(...))`，但更高效。

```julia-repl
julia> remotecall_fetch(r-> fetch(r)[1, 1], 2, r)
0.18526337335308085
```

这会在工作线程 2 上获取数组并返回第一个值。请注意，在这种情况下，`fetch` 不会移动任何数据，因为它是在拥有该数组的工作线程上执行的。还可以写：

```julia-repl
julia> remotecall_fetch(getindex, 2, r, 1, 1)
0.10824216411304866
```

记住 [`getindex(r,1,1)`](@ref) 是 [equivalent](@ref man-array-indexing) 到 `r[1,1]`，所以这个调用获取了未来 `r` 的第一个元素。

为了简化操作，可以将符号 `:any` 传递给 [`@spawnat`](@ref)，它会为您选择执行操作的位置：

```julia-repl
julia> r = @spawnat :any rand(2,2)
Future(2, 1, 4, nothing)

julia> s = @spawnat :any 1 .+ fetch(r)
Future(3, 1, 5, nothing)

julia> fetch(s)
2×2 Array{Float64,2}:
 1.38854  1.9098
 1.20939  1.57158
```

请注意，我们使用了 `1 .+ fetch(r)` 而不是 `1 .+ r`。这是因为我们不知道代码将在哪里运行，因此通常可能需要 [`fetch`](@ref) 将 `r` 移动到执行加法的进程中。在这种情况下，[`@spawnat`](@ref) 足够智能，可以在拥有 `r` 的进程上执行计算，因此 `4d61726b646f776e2e436f64652822222c202266657463682229_40726566` 将是一个无操作（没有工作被完成）。

（值得注意的是，[`@spawnat`](@ref) 不是内置的，而是在 Julia 中定义为 [macro](@ref man-macros)。你可以定义自己的此类构造。）

一个重要的事情是，一旦获取，[`Future`](@ref Distributed.Future) 将在本地缓存其值。进一步的 [`fetch`](@ref) 调用不需要网络跳转。一旦所有引用的 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` 都已获取，远程存储的值将被删除。

[`@async`](@ref) 类似于 [`@spawnat`](@ref)，但仅在本地进程上运行任务。我们用它为每个进程创建一个“馈送”任务。每个任务选择下一个需要计算的索引，然后等待其进程完成，然后重复，直到我们用完索引。请注意，馈送任务在主任务到达 [`@sync`](@ref) 块的末尾之前不会开始执行，此时它放弃控制并等待所有本地任务完成，然后再从函数返回。至于 v0.7 及以后的版本，馈送任务能够通过 `nextidx` 共享状态，因为它们都在同一个进程上运行。即使 `Tasks` 是以协作方式调度的，在某些上下文中仍然可能需要锁定，如在 [asynchronous I/O](@ref faq-async-io) 中。这意味着上下文切换仅在明确定义的点发生：在这种情况下，当调用 [`remotecall_fetch`](@ref) 时。这是当前实现的状态，未来的 Julia 版本可能会有所变化，因为它旨在使得在 M 个进程上运行最多 N 个 `Tasks` 成为可能，即 [M:N Threading](https://en.wikipedia.org/wiki/Thread_(computing)#Models)。然后将需要一个锁获取\释放模型来处理 `nextidx`，因为让多个进程同时读写资源是不安全的。

## [Code Availability and Loading Packages](@id code-availability)

您的代码必须在运行它的任何进程中可用。例如，在Julia提示符中输入以下内容：

```julia-repl
julia> function rand2(dims...)
           return 2*rand(dims...)
       end

julia> rand2(2,2)
2×2 Array{Float64,2}:
 0.153756  0.368514
 1.15119   0.918912

julia> fetch(@spawnat :any rand2(2,2))
ERROR: RemoteException(2, CapturedException(UndefVarError(Symbol("#rand2"))))
Stacktrace:
[...]
```

进程 1 知道函数 `rand2`，但进程 2 不知道。

最常见的情况是您将从文件或包中加载代码，并且您在控制哪些进程加载代码方面具有相当大的灵活性。考虑一个文件 `DummyModule.jl`，其中包含以下代码：

```julia
module DummyModule

export MyType, f

mutable struct MyType
    a::Int
end

f(x) = x^2+1

println("loaded")

end
```

为了在所有进程中引用 `MyType`，需要在每个进程上加载 `DummyModule.jl`。调用 `include("DummyModule.jl")` 仅在单个进程上加载它。要在每个进程上加载它，请使用 [`@everywhere`](@ref) 宏（以 `julia -p 2` 启动 Julia）：

```julia-repl
julia> @everywhere include("DummyModule.jl")
loaded
      From worker 3:    loaded
      From worker 2:    loaded
```

如往常一样，这并没有在任何进程中引入 `DummyModule` 的作用域，这需要 [`using`](@ref) 或 [`import`](@ref)。此外，当 `DummyModule` 在一个进程中被引入作用域时，它在其他任何进程中都没有：

```julia-repl
julia> using .DummyModule

julia> MyType(7)
MyType(7)

julia> fetch(@spawnat 2 MyType(7))
ERROR: On worker 2:
UndefVarError: `MyType` not defined in `Main`
⋮

julia> fetch(@spawnat 2 DummyModule.MyType(7))
MyType(7)
```

然而，例如，即使 `MyType` 不在作用域内，仍然可以将其发送到已加载 `DummyModule` 的进程：

```julia-repl
julia> put!(RemoteChannel(2), MyType(7))
RemoteChannel{Channel{Any}}(2, 1, 13)
```

一个文件也可以在启动时通过 `-L` 标志在多个进程上预加载，并且可以使用驱动脚本来驱动计算：

```
julia -p <n> -L file1.jl -L file2.jl driver.jl
```

在上述示例中运行驱动脚本的 Julia 进程的 `id` 等于 1，就像提供交互式提示的进程一样。

最后，如果 `DummyModule.jl` 不是一个独立文件而是一个包，那么 `using DummyModule` 将在所有进程中 *加载* `DummyModule.jl`，但仅在调用 [`using`](@ref) 的进程中将其引入作用域。

## Starting and managing worker processes

基础的 Julia 安装内置支持两种类型的集群：

  * 一个使用 `-p` 选项指定的本地集群，如上所示。
  * 一个跨机器的集群使用 `--machine-file` 选项。这使用无密码的 `ssh` 登录在指定的机器上启动 Julia 工作进程（从与当前主机相同的路径）。每个机器定义的格式为 `[count*][user@]host[:port] [bind_addr[:port]]`。`user` 默认为当前用户，`port` 默认为标准 ssh 端口。`count` 是要在节点上生成的工作进程数量，默认为 1。可选的 `bind-to bind_addr[:port]` 指定其他工作进程应使用的连接到此工作进程的 IP 地址和端口。

!!! note
    虽然 Julia 通常努力保持向后兼容，但将代码分发到工作进程依赖于 [`Serialization.serialize`](@ref)。正如相关文档中指出的，这在不同的 Julia 版本之间无法保证有效，因此建议所有机器上的所有工作进程使用相同的版本。


函数 [`addprocs`](@ref)、[`rmprocs`](@ref)、[`workers`](@ref) 和其他函数可作为编程手段，用于在集群中添加、移除和查询进程。

```julia-repl
julia> using Distributed

julia> addprocs(2)
2-element Array{Int64,1}:
 2
 3
```

模块 [`Distributed`](@ref man-distributed) 必须在调用 [`addprocs`](@ref) 之前在主进程中显式加载。它会自动在工作进程中可用。

!!! note
    请注意，工作进程不会运行 `~/.julia/config/startup.jl` 启动脚本，也不会与其他正在运行的进程同步其全局状态（例如命令行开关、全局变量、新方法定义和加载的模块）。您可以使用 `addprocs(exeflags="--project")` 来初始化具有特定环境的工作进程，然后使用 `@everywhere using <modulename>` 或 `@everywhere include("file.jl")`。


其他类型的集群可以通过编写自定义的 `ClusterManager` 来支持，如下文 [ClusterManagers](@ref) 部分所述。

## Data Movement

发送消息和移动数据构成了分布式程序中大部分的开销。减少发送的消息数量和数据量对于实现性能和可扩展性至关重要。为此，了解Julia各种分布式编程构造所执行的数据移动是很重要的。

[`fetch`](@ref) 可以被视为一种显式数据移动操作，因为它直接要求将一个对象移动到本地机器。[`@spawnat`](@ref)（以及一些相关构造）也移动数据，但这并不那么明显，因此可以称之为隐式数据移动操作。考虑这两种构造和平方随机矩阵的方法：

方法 1:

```julia-repl
julia> A = rand(1000,1000);

julia> Bref = @spawnat :any A^2;

[...]

julia> fetch(Bref);
```

方法 2：

```julia-repl
julia> Bref = @spawnat :any rand(1000,1000)^2;

[...]

julia> fetch(Bref);
```

这个差异看起来微不足道，但实际上由于 [`@spawnat`](@ref) 的行为而变得相当重要。在第一种方法中，随机矩阵在本地构造，然后发送到另一个进程进行平方。在第二种方法中，随机矩阵在另一个进程中构造并平方。因此，第二种方法发送的数据量远少于第一种。

在这个玩具示例中，这两种方法很容易区分和选择。然而，在一个真实的程序中，设计数据移动可能需要更多的思考，并且可能需要一些测量。例如，如果第一个进程需要矩阵 `A`，那么第一种方法可能更好。或者，如果计算 `A` 的成本很高，并且只有当前进程拥有它，那么将其移动到另一个进程可能是不可避免的。或者，如果当前进程在 [`@spawnat`](@ref) 和 `fetch(Bref)` 之间几乎没有事情可做，那么完全消除并行性可能更好。或者想象一下 `rand(1000,1000)` 被一个更昂贵的操作替代。那么，为了这个步骤添加另一个 `4d61726b646f776e2e436f64652822222c202240737061776e61742229_40726566` 语句可能是有意义的。

## Global variables

通过 [`@spawnat`](@ref) 远程执行的表达式，或使用 [`remotecall`](@ref) 指定的远程执行闭包可能会引用全局变量。模块 `Main` 下的全局绑定与其他模块中的全局绑定处理方式略有不同。考虑以下代码片段：

```julia-repl
A = rand(10,10)
remotecall_fetch(()->sum(A), 2)
```

In this case [`sum`](@ref) MUST be defined in the remote process. Note that `A` is a global variable defined in the local workspace. Worker 2 does not have a variable called `A` under `Main`. The act of shipping the closure `()->sum(A)` to worker 2 results in `Main.A` being defined on 2. `Main.A` continues to exist on worker 2 even after the call [`remotecall_fetch`](@ref) returns. Remote calls with embedded global references (under `Main` module only) manage globals as follows:

  * 如果在远程调用中引用目标工作者，则会创建新的全局绑定。
  * 全局常量在远程节点上也被声明为常量。
  * 全局变量仅在远程调用的上下文中重新发送到目标工作节点，并且仅在其值发生变化时才会发送。此外，集群不会在节点之间同步全局绑定。例如：

    ```julia
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 2) # worker 2
    A = rand(10,10)
    remotecall_fetch(()->sum(A), 3) # worker 3
    A = nothing
    ```

    执行上述代码片段会导致工作节点 2 上的 `Main.A` 与工作节点 3 上的 `Main.A` 值不同，而节点 1 上的 `Main.A` 值被设置为 `nothing`。

正如您可能已经意识到的，当全局变量在主节点上被重新分配时，相关的内存可能会被回收，但在工作节点上并不会采取这样的行动，因为绑定仍然有效。[`clear!`](@ref) 可以用于手动将远程节点上的特定全局变量重新分配为 `nothing`，一旦它们不再需要。这将释放与它们相关的任何内存，作为常规垃圾回收周期的一部分。

因此，程序在远程调用中引用全局变量时应谨慎。实际上，如果可能的话，最好完全避免使用它们。如果必须引用全局变量，请考虑使用 `let` 块来局部化全局变量。

例如：

```julia-repl
julia> A = rand(10,10);

julia> remotecall_fetch(()->A, 2);

julia> B = rand(10,10);

julia> let B = B
           remotecall_fetch(()->B, 2)
       end;

julia> @fetchfrom 2 InteractiveUtils.varinfo()
name           size summary
––––––––– ––––––––– ––––––––––––––––––––––
A         800 bytes 10×10 Array{Float64,2}
Base                Module
Core                Module
Main                Module
```

如可以看到，全球变量 `A` 在工作者 2 上定义，但 `B` 被捕获为局部变量，因此在工作者 2 上不存在 `B` 的绑定。

## Parallel Map and Loops

幸运的是，许多有用的并行计算不需要数据移动。一个常见的例子是蒙特卡罗模拟，其中多个进程可以同时处理独立的模拟试验。我们可以使用 [`@spawnat`](@ref) 在两个进程上抛硬币。首先，在 `count_heads.jl` 中编写以下函数：

```julia
function count_heads(n)
    c::Int = 0
    for i = 1:n
        c += rand(Bool)
    end
    c
end
```

函数 `count_heads` 只是将 `n` 个随机位相加。以下是我们如何在两台机器上进行一些试验，并将结果相加：

```julia-repl
julia> @everywhere include_string(Main, $(read("count_heads.jl", String)), "count_heads.jl")

julia> a = @spawnat :any count_heads(100000000)
Future(2, 1, 6, nothing)

julia> b = @spawnat :any count_heads(100000000)
Future(3, 1, 7, nothing)

julia> fetch(a)+fetch(b)
100001564
```

这个例子演示了一种强大且常用的并行编程模式。许多迭代在多个进程中独立运行，然后使用某个函数将它们的结果结合起来。这个组合过程称为*归约*，因为它通常是张量秩降低的：一组数字被减少为一个单一的数字，或者一个矩阵被减少为一行或一列，等等。在代码中，这通常看起来像模式 `x = f(x,v[i])`，其中 `x` 是累加器，`f` 是归约函数，而 `v[i]` 是正在被归约的元素。希望 `f` 是结合性的，这样操作的执行顺序就无关紧要。

注意到我们对 `count_heads` 的使用模式可以被推广。我们使用了两个显式的 [`@spawnat`](@ref) 语句，这限制了并行性为两个进程。为了在任意数量的进程上运行，我们可以使用 *并行 for 循环*，在分布式内存中运行，这可以用 Julia 这样写 [`@distributed`](@ref)：

```julia
nheads = @distributed (+) for i = 1:200000000
    Int(rand(Bool))
end
```

这个构造实现了将迭代分配给多个进程的模式，并将它们与指定的归约（在这种情况下是 `(+)`）结合起来。每次迭代的结果被视为循环内部最后一个表达式的值。整个并行循环表达式本身的结果就是最终答案。

请注意，尽管并行 for 循环看起来像串行 for 循环，但它们的行为截然不同。特别是，迭代不会按照指定的顺序发生，并且对变量或数组的写入在全局范围内不可见，因为迭代在不同的进程上运行。任何在并行循环中使用的变量将被复制并广播到每个进程。

例如，以下代码将无法按预期工作：

```julia
a = zeros(100000)
@distributed for i = 1:100000
    a[i] = i
end
```

此代码不会初始化所有的 `a`，因为每个进程将拥有它的单独副本。像这样的并行 for 循环必须避免。幸运的是，[Shared Arrays](@ref man-shared-arrays) 可以用来绕过这个限制：

```julia
using SharedArrays

a = SharedArray{Float64}(10)
@distributed for i = 1:10
    a[i] = i
end
```

在并行循环中使用“外部”变量是完全合理的，如果这些变量是只读的：

```julia
a = randn(1000)
@distributed (+) for i = 1:100000
    f(a[rand(1:end)])
end
```

在这里，每次迭代将 `f` 应用到一个随机选择的样本，该样本来自所有进程共享的向量 `a`。

如您所见，如果不需要，可以省略归约操作符。在这种情况下，循环异步执行，即在所有可用工作节点上生成独立任务，并立即返回一个数组 [`Future`](@ref Distributed.Future)，而无需等待完成。调用者可以通过稍后调用 [`fetch`](@ref) 来等待 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` 的完成，或者通过在循环末尾前缀 [`@sync`](@ref) 来等待完成，例如 `@sync @distributed for`。

在某些情况下，不需要减少运算符，我们仅希望将一个函数应用于某个范围内的所有整数（或者更一般地，应用于某个集合中的所有元素）。这是一种称为 *并行映射* 的有用操作，在 Julia 中实现为 [`pmap`](@ref) 函数。例如，我们可以如下并行计算几个大型随机矩阵的奇异值：

```julia-repl
julia> M = Matrix{Float64}[rand(1000,1000) for i = 1:10];

julia> pmap(svdvals, M);
```

Julia的 [`pmap`](@ref) 旨在处理每个函数调用都需要大量工作的情况。相比之下，`@distributed for` 可以处理每次迭代都很小的情况，可能仅仅是对两个数字求和。`4d61726b646f776e2e436f64652822222c2022706d61702229_40726566` 和 `@distributed for` 都仅使用工作进程进行并行计算。在 `@distributed for` 的情况下，最终的归约是在调用进程上完成的。

## Remote References and AbstractChannels

远程引用始终指向 `AbstractChannel` 的一个实现。

一个 `AbstractChannel`（如 `Channel`）的具体实现需要实现 [`put!`](@ref)、[`take!`](@ref)、[`fetch`](@ref)、[`isready`](@ref) 和 [`wait`](@ref)。由 [`Future`](@ref Distributed.Future) 引用的远程对象存储在 `Channel{Any}(1)` 中，即一个大小为 1 的 `Channel`，能够容纳 `Any` 类型的对象。

[`RemoteChannel`](@ref)，它是可重写的，可以指向任何类型和大小的通道，或任何其他 `AbstractChannel` 的实现。

构造函数 `RemoteChannel(f::Function, pid)()` 允许我们构造对持有特定类型多个值的通道的引用。`f` 是在 `pid` 上执行的函数，必须返回一个 `AbstractChannel`。

例如，`RemoteChannel(()->Channel{Int}(10), pid)` 将返回对类型为 `Int` 且大小为 10 的通道的引用。该通道存在于工作者 `pid` 上。

方法 [`put!`](@ref)、[`take!`](@ref)、[`fetch`](@ref)、[`isready`](@ref) 和 [`wait`](@ref) 在 [`RemoteChannel`](@ref) 上被代理到远程进程的后备存储。

[`RemoteChannel`](@ref) 因此可以用来引用用户实现的 `AbstractChannel` 对象。一个简单的例子是以下的 `DictChannel`，它使用字典作为其远程存储：

```jldoctest
julia> struct DictChannel{T} <: AbstractChannel{T}
           d::Dict
           cond_take::Threads.Condition    # waiting for data to become available
           DictChannel{T}() where {T} = new(Dict(), Threads.Condition())
           DictChannel() = DictChannel{Any}()
       end

julia> begin
       function Base.put!(D::DictChannel, k, v)
           @lock D.cond_take begin
               D.d[k] = v
               notify(D.cond_take)
           end
           return D
       end
       function Base.take!(D::DictChannel, k)
           @lock D.cond_take begin
               v = fetch(D, k)
               delete!(D.d, k)
               return v
           end
       end
       Base.isready(D::DictChannel) = @lock D.cond_take !isempty(D.d)
       Base.isready(D::DictChannel, k) = @lock D.cond_take haskey(D.d, k)
       function Base.fetch(D::DictChannel, k)
           @lock D.cond_take begin
               wait(D, k)
               return D.d[k]
           end
       end
       function Base.wait(D::DictChannel, k)
           @lock D.cond_take begin
               while !isready(D, k)
                   wait(D.cond_take)
               end
           end
       end
       end;

julia> d = DictChannel();

julia> isready(d)
false

julia> put!(d, :k, :v);

julia> isready(d, :k)
true

julia> fetch(d, :k)
:v

julia> wait(d, :k)

julia> take!(d, :k)
:v

julia> isready(d, :k)
false
```

## Channels and RemoteChannels

  * 一个 [`Channel`](@ref) 是本地于一个进程的。工作者 2 不能直接引用工作者 3 上的 `4d61726b646f776e2e436f64652822222c20224368616e6e656c2229_40726566`，反之亦然。然而，一个 [`RemoteChannel`](@ref) 可以在工作者之间放置和获取值。
  * 一个 [`RemoteChannel`](@ref) 可以被视为一个 *句柄*，指向 [`Channel`](@ref)。
  * 与 [`RemoteChannel`](@ref) 相关的进程 ID `pid` 确定了后备存储的进程，即后备 [`Channel`](@ref) 存在的进程。
  * 任何与 [`RemoteChannel`](@ref) 相关的进程都可以从通道中放入和取出物品。数据会自动发送到（或从）与 `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` 关联的进程。
  * 序列化 [`Channel`](@ref) 也会序列化通道中存在的任何数据。因此，反序列化实际上会有效地复制原始对象。
  * 另一方面，序列化 [`RemoteChannel`](@ref) 仅涉及序列化一个标识符，该标识符标识了由句柄引用的 [`Channel`](@ref) 的位置和实例。因此，反序列化的 `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` 对象（在任何工作者上）也指向与原始对象相同的后备存储。

上述的通道示例可以修改为进程间通信，如下所示。

我们启动 4 个工作者来处理一个单一的 `jobs` 远程通道。作业通过一个 id (`job_id`) 被写入通道。这个模拟中的每个远程执行任务读取一个 `job_id`，等待随机的时间，然后将 `job_id`、所用时间和它自己的 `pid` 作为元组写回结果通道。最后，所有的 `results` 在主进程中被打印出来。

```julia-repl
julia> addprocs(4); # add worker processes

julia> const jobs = RemoteChannel(()->Channel{Int}(32));

julia> const results = RemoteChannel(()->Channel{Tuple}(32));

julia> @everywhere function do_work(jobs, results) # define work function everywhere
           while true
               job_id = take!(jobs)
               exec_time = rand()
               sleep(exec_time) # simulates elapsed time doing actual work
               put!(results, (job_id, exec_time, myid()))
           end
       end

julia> function make_jobs(n)
           for i in 1:n
               put!(jobs, i)
           end
       end;

julia> n = 12;

julia> errormonitor(@async make_jobs(n)); # feed the jobs channel with "n" jobs

julia> for p in workers() # start tasks on the workers to process requests in parallel
           remote_do(do_work, p, jobs, results)
       end

julia> @elapsed while n > 0 # print out results
           job_id, exec_time, where = take!(results)
           println("$job_id finished in $(round(exec_time; digits=2)) seconds on worker $where")
           global n = n - 1
       end
1 finished in 0.18 seconds on worker 4
2 finished in 0.26 seconds on worker 5
6 finished in 0.12 seconds on worker 4
7 finished in 0.18 seconds on worker 4
5 finished in 0.35 seconds on worker 5
4 finished in 0.68 seconds on worker 2
3 finished in 0.73 seconds on worker 3
11 finished in 0.01 seconds on worker 3
12 finished in 0.02 seconds on worker 3
9 finished in 0.26 seconds on worker 5
8 finished in 0.57 seconds on worker 4
10 finished in 0.58 seconds on worker 2
0.055971741
```

### Remote References and Distributed Garbage Collection

通过远程引用引用的对象只能在集群中*所有*持有的引用被删除后才能释放。

存储值的节点跟踪哪些工作者对其有引用。每当一个 [`RemoteChannel`](@ref) 或一个（未获取的） [`Future`](@ref Distributed.Future) 被序列化到一个工作者时，引用所指向的节点会被通知。每当一个 `4d61726b646f776e2e436f64652822222c202252656d6f74654368616e6e656c2229_40726566` 或一个（未获取的） `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` 在本地被垃圾收集时，拥有该值的节点再次被通知。这是在一个内部集群感知的序列化器中实现的。远程引用仅在运行集群的上下文中有效。不支持将引用序列化和反序列化为常规 `IO` 对象。

通知是通过发送“跟踪”消息来完成的——当引用被序列化到不同的进程时发送“添加引用”消息，当引用在本地被垃圾收集时发送“删除引用”消息。

由于 [`Future`](@ref Distributed.Future) 是一次性写入并在本地缓存的，因此 [`fetch`](@ref) 一个 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` 也会更新拥有该值的节点上的引用跟踪信息。

拥有该值的节点在所有引用被清除后释放它。

使用 [`Future`](@ref Distributed.Future)，将已经获取的 `4d61726b646f776e2e436f64652822222c20224675747572652229_407265662044697374726962757465642e467574757265` 序列化到不同的节点时，也会发送该值，因为原始远程存储可能在此时已经收集了该值。

重要的是要注意，*何时* 对象被局部垃圾回收取决于对象的大小和系统当前的内存压力。

In case of remote references, the size of the local reference object is quite small, while the value stored on the remote node may be quite large. Since the local object may not be collected immediately, it is a good practice to explicitly call [`finalize`](@ref) on local instances of a [`RemoteChannel`](@ref), or on unfetched [`Future`](@ref Distributed.Future)s. Since calling [`fetch`](@ref) on a [`Future`](@ref Distributed.Future) also removes its reference from the remote store, this is not required on fetched [`Future`](@ref Distributed.Future)s. Explicitly calling [`finalize`](@ref) results in an immediate message sent to the remote node to go ahead and remove its reference to the value.

一旦最终确定，引用将变为无效，无法在任何进一步的调用中使用。

## Local invocations

数据必须被复制到远程节点以进行执行。这适用于远程调用和当数据存储到 [`RemoteChannel`](@ref) / [`Future`](@ref Distributed.Future) 在不同节点上的情况。如预期的那样，这导致在远程节点上复制序列化对象。然而，当目标节点是本地节点时，即调用进程 ID 与远程节点 ID 相同，它将作为本地调用执行。它通常（但并不总是）在不同的任务中执行 - 但数据没有序列化/反序列化。因此，调用引用的是传递的相同对象实例 - 不会创建副本。下面强调了这种行为：

```julia-repl
julia> using Distributed;

julia> rc = RemoteChannel(()->Channel(3));   # RemoteChannel created on local node

julia> v = [0];

julia> for i in 1:3
           v[1] = i                          # Reusing `v`
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[3], [3], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 1

julia> addprocs(1);

julia> rc = RemoteChannel(()->Channel(3), workers()[1]);   # RemoteChannel created on remote node

julia> v = [0];

julia> for i in 1:3
           v[1] = i
           put!(rc, v)
       end;

julia> result = [take!(rc) for _ in 1:3];

julia> println(result);
Array{Int64,1}[[1], [2], [3]]

julia> println("Num Unique objects : ", length(unique(map(objectid, result))));
Num Unique objects : 3
```

如可以看到，[`put!`](@ref) 在一个本地拥有的 [`RemoteChannel`](@ref) 上，使用相同的对象 `v` 在调用之间进行修改，结果是存储了相同的单个对象实例。与此相对的是，当拥有 `rc` 的节点是不同节点时，会创建 `v` 的副本。

需要注意的是，这通常不是一个问题。只有在对象既被本地存储又在调用后被修改时，才需要考虑这一点。在这种情况下，存储对象的 `deepcopy` 可能是合适的。

这对于本地节点上的远程调用也是如此，如下例所示：

```julia-repl
julia> using Distributed; addprocs(1);

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), myid(), v);     # Executed on local node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[1], v2=[1], true

julia> v = [0];

julia> v2 = remotecall_fetch(x->(x[1] = 1; x), workers()[1], v); # Executed on remote node

julia> println("v=$v, v2=$v2, ", v === v2);
v=[0], v2=[1], false
```

如再次所示，对本地节点的远程调用表现得就像直接调用一样。该调用修改作为参数传递的本地对象。在远程调用中，它对参数的副本进行操作。

一般来说，这不是一个问题。如果本地节点也被用作计算节点，并且在调用后使用的参数需要考虑这种行为，并且如果需要，必须将参数的深拷贝传递给在本地节点上调用的函数。对远程节点的调用将始终在参数的副本上操作。

## [Shared Arrays](@id man-shared-arrays)

共享数组使用系统共享内存在多个进程之间映射相同的数组。当您希望在同一台机器上的两个或多个进程之间共同访问大量数据时，[`SharedArray`](@ref) 是一个不错的选择。共享数组支持通过模块 `SharedArrays` 提供，必须在所有参与的工作进程中显式加载。

一个互补的数据结构由外部包 [`DistributedArrays.jl`](https://github.com/JuliaParallel/DistributedArrays.jl) 提供，形式为 `DArray`。虽然与 [`SharedArray`](@ref) 有一些相似之处，但 [`DArray`](https://github.com/JuliaParallel/DistributedArrays.jl) 的行为却大相径庭。在 `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` 中，每个“参与”进程都可以访问整个数组；而在 `4d61726b646f776e2e436f64652822222c20224441727261792229_68747470733a2f2f6769746875622e636f6d2f4a756c6961506172616c6c656c2f44697374726962757465644172726179732e6a6c` 中，每个进程仅能本地访问一块数据，且没有两个进程共享同一块数据。

[`SharedArray`](@ref) 索引（赋值和访问值）与常规数组的工作方式完全相同，并且效率高，因为底层内存对本地进程是可用的。因此，大多数算法在 `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` 上自然工作，尽管是在单进程模式下。在算法坚持使用 [`Array`](@ref) 输入的情况下，可以通过调用 [`sdata`](@ref) 从 `4d61726b646f776e2e436f64652822222c202253686172656441727261792229_40726566` 中检索底层数组。对于其他 `AbstractArray` 类型，`4d61726b646f776e2e436f64652822222c202273646174612229_40726566` 仅返回对象本身，因此在任何 `Array` 类型对象上使用 `4d61726b646f776e2e436f64652822222c202273646174612229_40726566` 是安全的。

共享数组的构造函数形式为：

```julia
SharedArray{T,N}(dims::NTuple; init=false, pids=Int[])
```

创建一个 `N` 维的共享数组，类型为 `T`，大小为 `dims`，并在由 `pids` 指定的进程之间共享。与分布式数组不同，共享数组仅可由那些参与的工作者访问，这些工作者由 `pids` 命名参数指定（如果创建进程在同一主机上，也可以访问）。请注意，只有 [`isbits`](@ref) 的元素在 SharedArray 中是支持的。

如果指定了一个签名为 `initfn(S::SharedArray)` 的 `init` 函数，它将在所有参与的工作节点上被调用。您可以指定每个工作节点在数组的不同部分上运行 `init` 函数，从而实现初始化的并行化。

请提供您想要翻译的Markdown内容。

```julia-repl
julia> using Distributed

julia> addprocs(3)
3-element Array{Int64,1}:
 2
 3
 4

julia> @everywhere using SharedArrays

julia> S = SharedArray{Int,2}((3,4), init = S -> S[localindices(S)] = repeat([myid()], length(localindices(S))))
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  3  4  4

julia> S[3,2] = 7
7

julia> S
3×4 SharedArray{Int64,2}:
 2  2  3  4
 2  3  3  4
 2  7  4  4
```

[`SharedArrays.localindices`](@ref) 提供不相交的一维索引范围，有时方便在进程之间分配任务。当然，您可以按照任何您希望的方式划分工作：

```julia-repl
julia> S = SharedArray{Int,2}((3,4), init = S -> S[indexpids(S):length(procs(S)):length(S)] = repeat([myid()], length( indexpids(S):length(procs(S)):length(S))))
3×4 SharedArray{Int64,2}:
 2  2  2  2
 3  3  3  3
 4  4  4  4
```

由于所有进程都可以访问底层数据，因此您必须小心不要设置冲突。例如：

```julia
@sync begin
    for p in procs(S)
        @async begin
            remotecall_wait(fill!, p, S, p)
        end
    end
end
```

会导致未定义行为。因为每个进程用自己的 `pid` 填充 *整个* 数组，所以最后执行的进程（对于 `S` 的任何特定元素）将保留其 `pid`。

作为一个更长且复杂的示例，考虑并行运行以下“内核”：

```julia
q[i,j,t+1] = q[i,j,t] + u[i,j,t]
```

在这种情况下，如果我们尝试使用一维索引来分配工作，我们很可能会遇到麻烦：如果 `q[i,j,t]` 接近分配给一个工人的块的末尾，而 `q[i,j,t+1]` 接近分配给另一个工人的块的开头，那么 `q[i,j,t]` 很可能在计算 `q[i,j,t+1]` 时还没有准备好。在这种情况下，手动分块数组会更好。让我们沿着第二个维度进行分割。定义一个函数，返回分配给这个工人的 `(irange, jrange)` 索引：

```julia-repl
julia> @everywhere function myrange(q::SharedArray)
           idx = indexpids(q)
           if idx == 0 # This worker is not assigned a piece
               return 1:0, 1:0
           end
           nchunks = length(procs(q))
           splits = [round(Int, s) for s in range(0, stop=size(q,2), length=nchunks+1)]
           1:size(q,1), splits[idx]+1:splits[idx+1]
       end
```

接下来，定义内核：

```julia-repl
julia> @everywhere function advection_chunk!(q, u, irange, jrange, trange)
           @show (irange, jrange, trange)  # display so we can see what's happening
           for t in trange, j in jrange, i in irange
               q[i,j,t+1] = q[i,j,t] + u[i,j,t]
           end
           q
       end
```

我们还为 `SharedArray` 实现定义了一个便利包装器。

```julia-repl
julia> @everywhere advection_shared_chunk!(q, u) =
           advection_chunk!(q, u, myrange(q)..., 1:size(q,3)-1)
```

现在让我们比较三个不同的版本，其中一个在单个进程中运行：

```julia-repl
julia> advection_serial!(q, u) = advection_chunk!(q, u, 1:size(q,1), 1:size(q,2), 1:size(q,3)-1);
```

一个使用 [`@distributed`](@ref) 的。

```julia-repl
julia> function advection_parallel!(q, u)
           for t = 1:size(q,3)-1
               @sync @distributed for j = 1:size(q,2)
                   for i = 1:size(q,1)
                       q[i,j,t+1]= q[i,j,t] + u[i,j,t]
                   end
               end
           end
           q
       end;
```

并且一个分块委托的：

```julia-repl
julia> function advection_shared!(q, u)
           @sync begin
               for p in procs(q)
                   @async remotecall_wait(advection_shared_chunk!, p, q, u)
               end
           end
           q
       end;
```

如果我们创建 `SharedArray` 并对这些函数进行计时，我们会得到以下结果（使用 `julia -p 4`）：

```julia-repl
julia> q = SharedArray{Float64,3}((500,500,500));

julia> u = SharedArray{Float64,3}((500,500,500));
```

运行函数一次以进行 JIT 编译，并在第二次运行时 [`@time`](@ref) 它们：

```julia-repl
julia> @time advection_serial!(q, u);
(irange,jrange,trange) = (1:500,1:500,1:499)
 830.220 milliseconds (216 allocations: 13820 bytes)

julia> @time advection_parallel!(q, u);
   2.495 seconds      (3999 k allocations: 289 MB, 2.09% gc time)

julia> @time advection_shared!(q,u);
        From worker 2:       (irange,jrange,trange) = (1:500,1:125,1:499)
        From worker 4:       (irange,jrange,trange) = (1:500,251:375,1:499)
        From worker 3:       (irange,jrange,trange) = (1:500,126:250,1:499)
        From worker 5:       (irange,jrange,trange) = (1:500,376:500,1:499)
 238.119 milliseconds (2264 allocations: 169 KB)
```

`advection_shared!` 的最大优势在于它最小化了工作者之间的流量，使每个工作者能够在分配的任务上进行更长时间的计算。

### Shared Arrays and Distributed Garbage Collection

像远程引用一样，共享数组也依赖于创建节点的垃圾回收，以释放所有参与工作者的引用。创建许多短生命周期共享数组对象的代码将受益于尽快显式终结这些对象。这将导致内存和文件句柄映射共享段的释放更早。

## ClusterManagers

启动、管理和网络化 Julia 进程到一个逻辑集群是通过集群管理器完成的。`ClusterManager` 负责

  * 在集群环境中启动工作进程
  * 在每个工作者的生命周期中管理事件
  * 可选地，提供数据传输

一个Julia集群具有以下特征：

  * 初始的 Julia 进程，也称为 `master`，是特殊的，具有 `id` 为 1。
  * 只有 `master` 进程可以添加或移除工作进程。
  * 所有进程可以直接相互通信。

通过以下方式建立工人之间的连接（使用内置的 TCP/IP 传输）：

  * [`addprocs`](@ref) 被调用在主进程中，使用 `ClusterManager` 对象。
  * [`addprocs`](@ref) 调用适当的 [`launch`](@ref) 方法，该方法在适当的机器上生成所需数量的工作进程。
  * 每个工作者开始在一个空闲端口上监听，并将其主机和端口信息写入 [`stdout`](@ref)。
  * 集群管理器捕获每个工作节点的 [`stdout`](@ref) 并将其提供给主进程。
  * 主进程解析这些信息并为每个工作进程建立 TCP/IP 连接。
  * 每个工作节点也会通知集群中的其他工作节点。
  * 每个工人都连接到所有 `id` 小于自己 `id` 的工人。
  * 通过这种方式，建立了一个网状网络，其中每个工作者都与其他每个工作者直接连接。

虽然默认的传输层使用的是纯 [`TCPSocket`](@ref)，但Julia集群可以提供自己的传输方式。

Julia 提供了两个内置的集群管理器：

  * `LocalManager`，用于当调用 [`addprocs()`](@ref) 或 [`addprocs(np::Integer)`](@ref) 时
  * `SSHManager`，在调用 [`addprocs(hostnames::Array)`](@ref) 并传入主机名列表时使用。

`LocalManager` 用于在同一主机上启动额外的工作进程，从而利用多核和多处理器硬件。

因此，一个最小的集群管理器需要：

  * 成为抽象 `ClusterManager` 的子类型
  * 实现 [`launch`](@ref)，一个负责启动新工作者的方法。
  * 实现 [`manage`](@ref)，该函数在工人生命周期的各个事件中被调用（例如，发送中断信号）

[`addprocs(manager::FooManager)`](@ref addprocs) 需要 `FooManager` 实现：

```julia
function launch(manager::FooManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

作为一个例子，让我们看看负责在同一主机上启动工作者的 `LocalManager` 是如何实现的：

```julia
struct LocalManager <: ClusterManager
    np::Integer
end

function launch(manager::LocalManager, params::Dict, launched::Array, c::Condition)
    [...]
end

function manage(manager::LocalManager, id::Integer, config::WorkerConfig, op::Symbol)
    [...]
end
```

[`launch`](@ref) 方法接受以下参数：

  * `manager::ClusterManager`：调用 [`addprocs`](@ref) 的集群管理器
  * `params::Dict`: 所有传递给 [`addprocs`](@ref) 的关键字参数
  * `launched::Array`：要附加一个或多个 `WorkerConfig` 对象的数组
  * `c::Condition`：条件变量，用于在工作线程启动时进行通知。

[`launch`](@ref) 方法在一个单独的任务中异步调用。该任务的终止信号表示所有请求的工作者已经启动。因此，`4d61726b646f64652822222c20226c61756e63682229_40726566` 函数必须在所有请求的工作者启动后尽快退出。

新启动的工作进程以全互联的方式相互连接，并与主进程连接。指定命令行参数 `--worker[=<cookie>]` 会导致启动的进程初始化为工作进程，并通过 TCP/IP 套接字建立连接。

所有集群中的工作节点与主节点共享相同的 [cookie](@ref man-cluster-cookie)。当未指定 cookie 时，即使用 `--worker` 选项，工作节点会尝试从其标准输入读取它。`LocalManager` 和 `SSHManager` 都通过其标准输入将 cookie 传递给新启动的工作节点。

默认情况下，工作进程将在通过调用 [`getipaddr()`](@ref) 返回的地址上的空闲端口上监听。可以通过可选参数 `--bind-to bind_addr[:port]` 指定要监听的特定地址。这对于多宿主主机非常有用。

作为非TCP/IP传输的一个例子，某个实现可能选择使用MPI，在这种情况下，`--worker` 绝不能被指定。相反，新启动的工作者应该在使用任何并行构造之前调用 `init_worker(cookie)`。

对于每个启动的工作者，[`launch`](@ref) 方法必须将一个 `WorkerConfig` 对象（初始化了适当的字段）添加到 `launched` 中。

```julia
mutable struct WorkerConfig
    # Common fields relevant to all cluster managers
    io::Union{IO, Nothing}
    host::Union{AbstractString, Nothing}
    port::Union{Integer, Nothing}

    # Used when launching additional workers at a host
    count::Union{Int, Symbol, Nothing}
    exename::Union{AbstractString, Cmd, Nothing}
    exeflags::Union{Cmd, Nothing}

    # External cluster managers can use this to store information at a per-worker level
    # Can be a dict if multiple fields need to be stored.
    userdata::Any

    # SSHManager / SSH tunnel connections to workers
    tunnel::Union{Bool, Nothing}
    bind_addr::Union{AbstractString, Nothing}
    sshflags::Union{Cmd, Nothing}
    max_parallel::Union{Integer, Nothing}

    # Used by Local/SSH managers
    connect_at::Any

    [...]
end
```

`WorkerConfig` 中的大多数字段由内置管理器使用。自定义集群管理器通常只会指定 `io` 或 `host` / `port`：

  * 如果指定了 `io`，则用于读取主机/端口信息。Julia 工作进程在启动时会打印出其绑定地址和端口。这允许 Julia 工作进程监听任何可用的空闲端口，而不需要手动配置工作进程端口。
  * 如果未指定 `io`，则使用 `host` 和 `port` 进行连接。
  * `count`、`exename` 和 `exeflags` 与从一个工作者启动额外工作者相关。例如，集群管理器可以在每个节点上启动一个工作者，并利用该工作者启动额外的工作者。

      * `count` 与整数值 `n` 一起将启动总共 `n` 个工作者。
      * `count` 的值为 `:auto` 时，将启动与该机器上的 CPU 线程（逻辑核心）数量相同的工作进程。
      * `exename` 是 `julia` 可执行文件的名称，包括完整路径。
      * `exeflags` 应设置为新工作者所需的命令行参数。
  * `tunnel`、`bind_addr`、`sshflags` 和 `max_parallel` 在需要通过 SSH 隧道从主进程连接到工作进程时使用。
  * `userdata` 用于自定义集群管理器存储他们自己的工作特定信息。

`manage(manager::FooManager, id::Integer, config::WorkerConfig, op::Symbol)` 在工作者的生命周期中以适当的 `op` 值在不同的时间被调用：

  * 使用 `:register`/`:deregister` 当工作者被添加到/从 Julia 工作者池中移除时。
  * 使用 `:interrupt` 当调用 `interrupt(workers)` 时。`ClusterManager` 应该向适当的工作线程发送中断信号。
  * 使用 `:finalize` 进行清理。

### Cluster Managers with Custom Transports

将默认的 TCP/IP 全连接套接字替换为自定义传输层稍微复杂一些。每个 Julia 进程与其连接的工作进程有相同数量的通信任务。例如，考虑一个由 32 个进程组成的 Julia 集群，处于全连接的网状网络中：

  * 每个 Julia 进程因此有 31 个通信任务。
  * 每个任务在消息处理循环中处理来自单个远程工作者的所有传入消息。
  * 消息处理循环在一个 `IO` 对象上等待（例如，在默认实现中，一个 [`TCPSocket`](@ref)），读取整个消息，处理它并等待下一个消息。
  * 将消息发送到进程是通过任何 Julia 任务直接完成的——不仅仅是通信任务——再次通过适当的 `IO` 对象。

替换默认传输需要新的实现设置与远程工作者的连接，并提供适当的 `IO` 对象，以便消息处理循环可以等待。需要实现的特定于管理器的回调是：

```julia
connect(manager::FooManager, pid::Integer, config::WorkerConfig)
kill(manager::FooManager, pid::Int, config::WorkerConfig)
```

默认实现（使用 TCP/IP 套接字）被实现为 `connect(manager::ClusterManager, pid::Integer, config::WorkerConfig)`。

`connect` 应返回一对 `IO` 对象，一个用于读取来自工作进程 `pid` 发送的数据，另一个用于写入需要发送到工作进程 `pid` 的数据。自定义集群管理器可以使用内存中的 `BufferStream` 作为管道，在自定义的、可能不是 `IO` 的传输和 Julia 内置的并行基础设施之间代理数据。

一个 `BufferStream` 是一个内存中的 [`IOBuffer`](@ref)，它的行为类似于 `IO`——它是一个可以异步处理的流。

文件夹 `clustermanager/0mq` 在 [Examples repository](https://github.com/JuliaAttic/Examples) 中包含了一个使用 ZeroMQ 连接 Julia 工作进程的示例，采用星型拓扑结构，中间有一个 0MQ 代理。注意：Julia 进程仍然是 *逻辑上* 互相连接的——任何工作进程都可以直接向任何其他工作进程发送消息，而无需意识到 0MQ 被用作传输层。

当使用自定义传输时：

  * Julia workers 必须不要使用 `--worker` 启动。使用 `--worker` 启动将导致新启动的工作进程默认使用 TCP/IP 套接字传输实现。
  * 对于每个与工作者的传入逻辑连接，必须调用 `Base.process_messages(rd::IO, wr::IO)()`。这会启动一个新任务，处理从工作者读取和写入消息，工作者由 `IO` 对象表示。
  * `init_worker(cookie, manager::FooManager)` *必须* 在工作进程初始化时调用。
  * 字段 `connect_at::Any` 在 `WorkerConfig` 中可以由集群管理器设置，当调用 [`launch`](@ref) 时。该字段的值会在所有 [`connect`](@ref) 回调中传递。通常，它携带有关 *如何连接* 到工作者的信息。例如，TCP/IP 套接字传输使用此字段来指定连接到工作者的 `(host, port)` 元组。

`kill(manager, pid, config)` 被调用以从集群中移除一个工作者。在主进程中，必须通过实现关闭相应的 `IO` 对象以确保适当的清理。默认实现只是对指定的远程工作者执行 `exit()` 调用。

示例文件夹 `clustermanager/simple` 是一个示例，展示了使用 UNIX 域套接字进行集群设置的简单实现。

### Network Requirements for LocalManager and SSHManager

Julia 集群旨在在已经安全的环境中执行，例如本地笔记本电脑、部门集群或甚至云端。本节涵盖内置 `LocalManager` 和 `SSHManager` 的网络安全要求：

  * 主进程不监听任何端口。它只与工作进程建立连接。
  * 每个工作线程仅绑定到一个本地接口，并在操作系统分配的临时端口号上监听。
  * `LocalManager`，由 `addprocs(N)` 使用，默认仅绑定到回环接口。这意味着稍后在远程主机上启动的工作进程（或任何有恶意意图的人）无法连接到集群。`addprocs(4)` 后跟 `addprocs(["remote_host"])` 将会失败。一些用户可能需要创建一个由他们的本地系统和一些远程系统组成的集群。这可以通过显式请求 `LocalManager` 绑定到外部网络接口来完成，方法是使用 `restrict` 关键字参数：`addprocs(4; restrict=false)`。
  * `SSHManager`，由 `addprocs(list_of_remote_hosts)` 使用，通过 SSH 在远程主机上启动工作进程。默认情况下，SSH 仅用于启动 Julia 工作进程。后续的主-从和从-从连接使用普通的、未加密的 TCP/IP 套接字。远程主机必须启用无密码登录。可以通过关键字参数 `sshflags` 指定额外的 SSH 标志或凭据。
  * `addprocs(list_of_remote_hosts; tunnel=true, sshflags=<ssh keys and other flags>)` 在我们希望使用 SSH 连接进行主-从工作时非常有用。一个典型的场景是本地笔记本电脑运行 Julia REPL（即主节点），其余集群在云端，例如在 Amazon EC2 上。在这种情况下，只需在远程集群上打开 22 端口，并通过公钥基础设施（PKI）进行 SSH 客户端身份验证。身份验证凭据可以通过 `sshflags` 提供，例如 ```sshflags=`-i <keyfile>` ```.

    在全连接拓扑（默认情况下），所有工作节点通过普通的 TCP 套接字相互连接。因此，集群节点上的安全策略必须确保工作节点之间在临时端口范围内（根据操作系统不同而有所变化）自由连接。

    通过自定义 `ClusterManager` 可以实现对所有工作节点之间的流量（通过 SSH）进行安全和加密，或对单个消息进行加密。
  * 如果您将 `multiplex=true` 作为选项指定给 [`addprocs`](@ref)，则使用 SSH 多路复用在主控和工作节点之间创建隧道。如果您自己配置了 SSH 多路复用并且连接已经建立，则无论 `multiplex` 选项如何，都会使用 SSH 多路复用。如果启用了多路复用，则通过使用现有连接来设置转发（ssh 中的 `-O forward` 选项）。如果您的服务器需要密码认证，这将是有益的；您可以通过在 `4d61726b646f776e2e436f64652822222c202261646470726f63732229_40726566` 之前登录到服务器来避免在 Julia 中进行认证。控制套接字将在会话期间位于 `~/.ssh/julia-%r@%h:%p`，除非使用现有的多路复用连接。请注意，如果您在一个节点上创建多个进程并启用多路复用，则带宽可能会受到限制，因为在这种情况下，进程共享一个单一的多路复用 TCP 连接。

### [Cluster Cookie](@id man-cluster-cookie)

所有集群中的进程共享相同的 cookie，默认情况下，这是在主进程上随机生成的字符串：

  * [`cluster_cookie()`](@ref) 返回 cookie，而 `cluster_cookie(cookie)()` 设置它并返回新的 cookie。
  * 所有连接在双方都经过身份验证，以确保只有由主节点启动的工作者可以相互连接。
  * 该 cookie 可以在启动时通过参数 `--worker=<cookie>` 传递给工作进程。如果指定了参数 `--worker` 但没有提供 cookie，工作进程会尝试从其标准输入中读取 cookie ([`stdin`](@ref))。在获取 cookie 后，`stdin` 会立即关闭。
  * `ClusterManager`可以通过调用[`cluster_cookie()`](@ref)在主节点上检索cookie。未使用默认TCP/IP传输的集群管理器（因此未指定`--worker`）必须使用与主节点相同的cookie调用`init_worker(cookie, manager)`。

请注意，要求更高安全级别的环境可以通过自定义 `ClusterManager` 实现这一点。例如，cookie 可以预先共享，因此不需要作为启动参数指定。

## Specifying Network Topology (Experimental)

传递给 [`addprocs`](@ref) 的关键字参数 `topology` 用于指定工人之间的连接方式：

  * `:all_to_all`，默认设置：所有工作者彼此连接。
  * `:master_worker`：只有驱动程序进程，即 `pid` 1，才能与工作进程建立连接。
  * `:custom`: 集群管理器的 `launch` 方法通过 `WorkerConfig` 中的 `ident` 和 `connect_idents` 字段指定连接拓扑。具有集群管理器提供的身份 `ident` 的工作者将连接到 `connect_idents` 中指定的所有工作者。

关键字参数 `lazy=true|false` 仅影响 `topology` 选项 `:all_to_all`。如果为 `true`，集群将以主节点连接所有工作节点开始。特定的工作节点之间的连接在两个工作节点之间的第一次远程调用时建立。这有助于减少为集群内部通信分配的初始资源。连接的设置取决于并行程序的运行时需求。`lazy` 的默认值为 `true`。

目前，在未连接的工作者之间发送消息会导致错误。这种行为，以及功能和接口，应被视为实验性，可能会在未来的版本中发生变化。

## Noteworthy external packages

除了 Julia 的并行性，还有许多外部包值得一提。例如，[`MPI.jl`](https://github.com/JuliaParallel/MPI.jl) 是 `MPI` 协议的 Julia 封装，[`Dagger.jl`](https://github.com/JuliaParallel/Dagger.jl) 提供了类似于 Python 的 [Dask](https://dask.org/) 的功能，而 [`DistributedArrays.jl`](https://github.com/JuliaParallel/Distributedarrays.jl) 提供了在工作者之间分布的数组操作，正如 [outlined above](@ref man-shared-arrays)。

必须提到Julia的GPU编程生态系统，其中包括：

1. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) 封装了各种 CUDA 库，并支持为 Nvidia GPU 编译 Julia 内核。
2. [oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl) 封装了 oneAPI 统一编程模型，并支持在受支持的加速器上执行 Julia 内核。目前仅支持 Linux。
3. [AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl) 封装了 AMD ROCm 库，并支持为 AMD GPU 编译 Julia 内核。目前仅支持 Linux。
4. 高级库如 [KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl)、[Tullio.jl](https://github.com/mcabbott/Tullio.jl) 和 [ArrayFire.jl](https://github.com/JuliaComputing/ArrayFire.jl)。

在以下示例中，我们将使用 `DistributedArrays.jl` 和 `CUDA.jl` 通过首先通过 `distribute()` 和 `CuArray()` 将数组分发到多个进程。

记得在导入 `DistributedArrays.jl` 时，通过 [`@everywhere`](@ref) 在所有进程中导入它。

```julia-repl
$ ./julia -p 4

julia> addprocs()

julia> @everywhere using DistributedArrays

julia> using CUDA

julia> B = ones(10_000) ./ 2;

julia> A = ones(10_000) .* π;

julia> C = 2 .* A ./ B;

julia> all(C .≈ 4*π)
true

julia> typeof(C)
Array{Float64,1}

julia> dB = distribute(B);

julia> dA = distribute(A);

julia> dC = 2 .* dA ./ dB;

julia> all(dC .≈ 4*π)
true

julia> typeof(dC)
DistributedArrays.DArray{Float64,1,Array{Float64,1}}

julia> cuB = CuArray(B);

julia> cuA = CuArray(A);

julia> cuC = 2 .* cuA ./ cuB;

julia> all(cuC .≈ 4*π);
true

julia> typeof(cuC)
CuArray{Float64,1}
```

在以下示例中，我们将使用 `DistributedArrays.jl` 和 `CUDA.jl` 将一个数组分布到多个进程，并在其上调用一个通用函数。

```julia
function power_method(M, v)
    for i in 1:100
        v = M*v
        v /= norm(v)
    end

    return v, norm(M*v) / norm(v)  # or  (M*v) ./ v
end
```

`power_method` 重复创建一个新向量并对其进行归一化。我们在函数声明中没有指定任何类型签名，让我们看看它是否适用于上述数据类型：

```julia-repl
julia> M = [2. 1; 1 1];

julia> v = rand(2)
2-element Array{Float64,1}:
0.40395
0.445877

julia> power_method(M,v)
([0.850651, 0.525731], 2.618033988749895)

julia> cuM = CuArray(M);

julia> cuv = CuArray(v);

julia> curesult = power_method(cuM, cuv);

julia> typeof(curesult)
CuArray{Float64,1}

julia> dM = distribute(M);

julia> dv = distribute(v);

julia> dC = power_method(dM, dv);

julia> typeof(dC)
Tuple{DistributedArrays.DArray{Float64,1,Array{Float64,1}},Float64}
```

为了结束对外部包的简要介绍，我们可以考虑 `MPI.jl`，这是一个 MPI 协议的 Julia 包装器。由于考虑每个内部函数会花费太长时间，因此更好的是简单欣赏用于实现该协议的方法。

考虑这个玩具脚本，它简单地调用每个子进程，实例化它的排名，当达到主进程时，执行排名的总和。

```julia
import MPI

MPI.Init()

comm = MPI.COMM_WORLD
MPI.Barrier(comm)

root = 0
r = MPI.Comm_rank(comm)

sr = MPI.Reduce(r, MPI.SUM, root, comm)

if(MPI.Comm_rank(comm) == root)
   @printf("sum of ranks: %s\n", sr)
end

MPI.Finalize()
```

```
mpirun -np 4 ./julia example.jl
```

[^1]: In this context, MPI refers to the MPI-1 standard. Beginning with MPI-2, the MPI standards committee introduced a new set of communication mechanisms, collectively referred to as Remote Memory Access (RMA). The motivation for adding rma to the MPI standard was to facilitate one-sided communication patterns. For additional information on the latest MPI standard, see [https://mpi-forum.org/docs](https://mpi-forum.org/docs).
