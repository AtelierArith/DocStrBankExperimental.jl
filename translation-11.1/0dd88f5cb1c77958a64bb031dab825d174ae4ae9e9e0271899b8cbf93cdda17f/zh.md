# Profiling

`Profile` 模块提供了帮助开发者提高代码性能的工具。使用时，它会对运行中的代码进行测量，并生成输出，帮助您了解在单独行上花费了多少时间。最常见的用法是识别“瓶颈”，作为优化的目标。

`Profile` 实现了所谓的“采样”或 [statistical profiler](https://en.wikipedia.org/wiki/Profiling_(computer_programming))。它通过在执行任何任务期间定期进行回溯来工作。每个回溯捕获当前正在运行的函数和行号，以及导致此行的完整函数调用链，因此它是当前执行状态的“快照”。

如果你的运行时间大部分花费在执行某一特定代码行上，那么这一行将在所有回溯中频繁出现。换句话说，给定行的“成本”——或者说，到达并包括这一行的函数调用序列的成本——与它在所有回溯中出现的频率成正比。

采样分析器并不提供逐行的完整覆盖，因为回溯发生在间隔内（在Unix系统上默认是1毫秒，在Windows上是10毫秒，尽管实际调度受操作系统负载的影响）。此外，如下文进一步讨论的，由于样本是在所有执行点的稀疏子集上收集的，因此采样分析器收集的数据受到统计噪声的影响。

尽管存在这些限制，采样分析器仍然具有显著的优势：

  * 您无需对代码进行任何修改即可进行时间测量。
  * 它可以分析 Julia 的核心代码，甚至（可选地）分析 C 和 Fortran 库。
  * 通过“偶尔”运行，性能开销非常小；在分析时，您的代码几乎可以以原生速度运行。

出于这些原因，建议您在考虑任何替代方案之前，先尝试使用内置的采样分析器。

## Basic usage

让我们处理一个简单的测试用例：

```julia-repl
julia> function myfunc()
           A = rand(200, 200, 400)
           maximum(A)
       end
```

首先运行您打算分析的代码至少一次是个好主意（除非您想分析Julia的JIT编译器）：

```julia-repl
julia> myfunc() # run once to force compilation
```

现在我们准备对这个函数进行性能分析：

```julia-repl
julia> using Profile

julia> @profile myfunc()
```

要查看分析结果，有几种图形浏览器。一种“家族”可视化工具基于 [FlameGraphs.jl](https://github.com/timholy/FlameGraphs.jl)，每个家族成员提供不同的用户界面：

  * [VS Code](https://www.julia-vscode.org/) 是一个完整的集成开发环境，内置支持配置文件可视化。
  * [ProfileView.jl](https://github.com/timholy/ProfileView.jl) 是一个基于 GTK 的独立可视化工具。
  * [ProfileVega.jl](https://github.com/davidanthoff/ProfileVega.jl) 使用 VegaLight，并与 Jupyter 笔记本良好集成。
  * [StatProfilerHTML.jl](https://github.com/tkluck/StatProfilerHTML.jl) 生成 HTML，并提供一些额外的摘要，同时与 Jupyter 笔记本集成良好。
  * [ProfileSVG.jl](https://github.com/timholy/ProfileSVG.jl) 渲染 SVG
  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl) 提供一个本地网站，用于检查图表、火焰图等。
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) 是一个基于 HTML 画布的个人资料查看器 UI，使用于 [Julia VS Code extension](https://www.julia-vscode.org/)，但也可以生成交互式 HTML 文件。

一个完全独立的配置文件可视化方法是 [PProf.jl](https://github.com/vchuravy/PProf.jl)，它使用外部的 `pprof` 工具。

在这里，我们将使用标准库附带的基于文本的显示：

```julia-repl
julia> Profile.print()
80 ./event.jl:73; (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
 80 ./REPL.jl:97; macro expansion
  80 ./REPL.jl:66; eval_user_input(::Any, ::Base.REPL.REPLBackend)
   80 ./boot.jl:235; eval(::Module, ::Any)
    80 ./<missing>:?; anonymous
     80 ./profile.jl:23; macro expansion
      52 ./REPL[1]:2; myfunc()
       38 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type{B...
        38 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr{F...
       14 ./random.jl:278; rand
        14 ./random.jl:277; rand
         14 ./random.jl:366; rand
          14 ./random.jl:369; rand
      28 ./REPL[1]:3; myfunc()
       28 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinear,...
        3  ./reduce.jl:426; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
        25 ./reduce.jl:428; mapreduce_impl(::Base.#identity, ::Base.#scalarmax, ::Array{F...
```

每行显示代表代码中的一个特定位置（行号）。缩进用于表示函数调用的嵌套顺序，缩进更多的行在调用序列中更深。在每行中，第一个“字段”是*在此行或由此行执行的任何函数中*采样的回溯次数（样本数）。第二个字段是文件名和行号，第三个字段是函数名。请注意，具体的行号可能会随着Julia代码的变化而变化；如果您想要跟随，最好自己运行这个示例。

在这个例子中，我们可以看到顶层函数位于文件 `event.jl` 中。这个函数在你启动 Julia 时运行 REPL。如果你检查 `REPL.jl` 的第 97 行，你会看到这里调用了函数 `eval_user_input()`。这个函数用于评估你在 REPL 中输入的内容，由于我们在交互式工作，当我们输入 `@profile myfunc()` 时，这些函数被调用。下一行反映了在 [`@profile`](@ref) 宏中采取的操作。

第一行显示在 `event.jl` 的第 73 行进行了 80 次回溯，但并不是说这一行本身“昂贵”：第三行揭示所有这 80 次回溯实际上是在对 `eval_user_input` 的调用中触发的，等等。要找出哪些操作实际上耗费了时间，我们需要更深入地查看调用链。

第一行“重要”的内容是这一行：

```
52 ./REPL[1]:2; myfunc()
```

`REPL` 指的是我们在 REPL 中定义了 `myfunc`，而不是将其放在文件中；如果我们使用了文件，这里会显示文件名。`[1]` 表示函数 `myfunc` 是在这个 REPL 会话中评估的第一个表达式。`myfunc()` 的第 2 行包含对 `rand` 的调用，在这一行发生了 52 次（共 80 次）回溯。在下面，您可以看到在 `dSFMT.jl` 中调用了 `dsfmt_fill_array_close_open!`。

稍微往下，你会看到：

```
28 ./REPL[1]:3; myfunc()
```

`myfunc` 的第 3 行包含对 `maximum` 的调用，在这里共进行了 28 次（共 80 次）回溯。在下面，您可以看到 `base/reduce.jl` 中执行 `maximum` 函数的耗时操作的具体位置，适用于此类型的输入数据。

总体而言，我们可以初步得出结论，生成随机数的成本大约是寻找最大元素的两倍。我们可以通过收集更多样本来提高对这一结果的信心：

```julia-repl
julia> @profile (for i = 1:100; myfunc(); end)

julia> Profile.print()
[....]
 3821 ./REPL[1]:2; myfunc()
  3511 ./random.jl:431; rand!(::MersenneTwister, ::Array{Float64,3}, ::Int64, ::Type...
   3511 ./dSFMT.jl:84; dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_state, ::Ptr...
  310  ./random.jl:278; rand
   [....]
 2893 ./REPL[1]:3; myfunc()
  2893 ./reduce.jl:270; _mapreduce(::Base.#identity, ::Base.#scalarmax, ::IndexLinea...
   [....]
```

一般来说，如果你在一条线上收集了 `N` 个样本，你可以预期不确定性在 `sqrt(N)` 的数量级上（不考虑其他噪声源，比如计算机在处理其他任务时的繁忙程度）。这个规则的主要例外是垃圾回收，它运行不频繁但往往代价很高。（由于 Julia 的垃圾收集器是用 C 编写的，因此可以使用下面描述的 `C=true` 输出模式来检测此类事件，或者使用 [ProfileView.jl](https://github.com/timholy/ProfileView.jl)。）

这说明了默认的“树”转储；另一种选择是“扁平”转储，它独立于嵌套累积计数：

```julia-repl
julia> Profile.print(format=:flat)
 Count File          Line Function
  6714 ./<missing>     -1 anonymous
  6714 ./REPL.jl       66 eval_user_input(::Any, ::Base.REPL.REPLBackend)
  6714 ./REPL.jl       97 macro expansion
  3821 ./REPL[1]        2 myfunc()
  2893 ./REPL[1]        3 myfunc()
  6714 ./REPL[7]        1 macro expansion
  6714 ./boot.jl      235 eval(::Module, ::Any)
  3511 ./dSFMT.jl      84 dsfmt_fill_array_close_open!(::Base.dSFMT.DSFMT_s...
  6714 ./event.jl      73 (::Base.REPL.##1#2{Base.REPL.REPLBackend})()
  6714 ./profile.jl    23 macro expansion
  3511 ./random.jl    431 rand!(::MersenneTwister, ::Array{Float64,3}, ::In...
   310 ./random.jl    277 rand
   310 ./random.jl    278 rand
   310 ./random.jl    366 rand
   310 ./random.jl    369 rand
  2893 ./reduce.jl    270 _mapreduce(::Base.#identity, ::Base.#scalarmax, :...
     5 ./reduce.jl    420 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
   253 ./reduce.jl    426 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
  2592 ./reduce.jl    428 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
    43 ./reduce.jl    429 mapreduce_impl(::Base.#identity, ::Base.#scalarma...
```

如果你的代码包含递归，一个可能令人困惑的点是，在“子”函数中的一行代码可能会累积比总回溯更多的计数。考虑以下函数定义：

```julia
dumbsum(n::Integer) = n == 1 ? 1 : 1 + dumbsum(n-1)
dumbsum3() = dumbsum(3)
```

如果您要对 `dumbsum3` 进行分析，并且在执行 `dumbsum(1)` 时获取了回溯，回溯将如下所示：

```julia
dumbsum3
    dumbsum(3)
        dumbsum(2)
            dumbsum(1)
```

因此，这个子函数获得了3个计数，尽管父函数只获得了一个。“树”表示法使这一点更加清晰，因此（除了其他原因）它可能是查看结果的最有用方式。

## Accumulation and clearing

结果来自 [`@profile`](@ref) 累积在一个缓冲区；如果你在 `4d61726b646f776e2e436f64652822222c20224070726f66696c652229_40726566` 下运行多个代码片段，那么 [`Profile.print()`](@ref) 将显示你合并的结果。这可能非常有用，但有时你想要重新开始；你可以通过 [`Profile.clear()`](@ref) 来做到这一点。

## Options for controlling the display of profile results

[`Profile.print`](@ref) 提供了比我们迄今所描述的更多选项。让我们看看完整的声明：

```julia
function print(io::IO = stdout, data = fetch(); kwargs...)
```

让我们首先讨论两个位置参数，然后再讨论关键字参数：

  * `io` – 允许您将结果保存到缓冲区，例如文件，但默认情况下是打印到 `stdout`（控制台）。
  * `data` – 包含您想要分析的数据；默认情况下，这些数据来自 [`Profile.fetch()`](@ref)，该数据从预分配的缓冲区中提取回溯。例如，如果您想要分析分析器，您可以这样说：

    ```julia
    data = copy(Profile.fetch())
    Profile.clear()
    @profile Profile.print(stdout, data) # Prints the previous results
    Profile.print()                      # Prints results from Profile.print()
    ```

关键字参数可以是以下任意组合：

  * `format` – 上述介绍，决定是否以（默认，`:tree`）或不带（`:flat`）缩进指示树结构的方式打印回溯。
  * `C` – 如果为 `true`，则会显示来自 C 和 Fortran 代码的回溯（通常会被排除）。尝试使用 `Profile.print(C = true)` 运行入门示例。这在判断是 Julia 代码还是 C 代码导致瓶颈时非常有帮助；将 `C` 设置为 `true` 还会提高嵌套的可解释性，但会导致更长的性能分析输出。
  * `combine` – 一些代码行包含多个操作；例如，`s += A[i]` 同时包含数组引用（`A[i]`）和求和操作。这些对应于生成的机器代码中的不同行，因此在此行的回溯过程中可能会捕获两个或更多不同的地址。`combine = true` 将它们合并在一起，这可能是您通常想要的，但您可以通过将 `combine` 设置为 `false` 来为每个唯一的指令指针生成单独的输出。
  * `maxdepth` – 限制在 `:tree` 格式中深度高于 `maxdepth` 的帧。
  * `sortedby` – 控制 `:flat` 格式中的顺序。`:filefuncline`（默认）按源代码行排序，而 `:count` 按收集样本的数量排序。
  * `noisefloor` – 限制低于样本启发式噪声底线的帧（仅适用于格式 `:tree`）。建议尝试的值为 2.0（默认值为 0）。此参数隐藏 `n <= noisefloor * √N` 的样本，其中 `n` 是该行的样本数量，`N` 是被调用者的样本数量。
  * `mincount` – 限制出现次数少于 `mincount` 的帧。

文件/函数名称有时会被截断（用 `...` 表示），而缩进则用 `+n` 表示，`n` 是如果有空间可以插入的额外空格数量。如果你想要一个完整的深度嵌套代码的概况，通常一个好的主意是使用宽 `displaysize` 将其保存到文件中，方法是使用 [`IOContext`](@ref)：

```julia
open("/tmp/prof.txt", "w") do s
    Profile.print(IOContext(s, :displaysize => (24, 500)))
end
```

## Configuration

[`@profile`](@ref) 仅仅累积回溯，分析发生在你调用 [`Profile.print()`](@ref) 时。对于长时间运行的计算，预分配的用于存储回溯的缓冲区可能会被填满。如果发生这种情况，回溯将停止，但你的计算将继续。因此，你可能会错过一些重要的分析数据（当发生这种情况时，你会收到警告）。

您可以通过以下方式获取和配置相关参数：

```julia
Profile.init() # returns the current settings
Profile.init(n = 10^7, delay = 0.01)
```

`n` 是您可以存储的指令指针的总数，默认值为 `10^6`。如果您的典型回溯是 20 个指令指针，那么您可以收集 50000 个回溯，这表明统计不确定性小于 1%。这对于大多数应用程序来说可能已经足够了。

因此，您更有可能需要修改 `delay`，以秒为单位，设置 Julia 在快照之间执行请求计算所需的时间。一个运行时间很长的任务可能不需要频繁的回溯。默认设置为 `delay = 0.001`。当然，您可以减少延迟，也可以增加延迟；然而，一旦延迟变得与进行回溯所需的时间相似（在作者的笔记本电脑上约为 30 微秒），性能分析的开销就会增加。

## Memory allocation analysis

提高性能的最常见技术之一是减少内存分配。Julia 提供了几种工具来测量这一点：

### `@time`

分配的总量可以通过 [`@time`](@ref)、[`@allocated`](@ref) 和 [`@allocations`](@ref) 来测量，特定的触发分配的行通常可以通过分析这些行所产生的垃圾回收成本来推断。然而，有时直接测量每行代码分配的内存量更为高效。

### GC Logging

虽然 [`@time`](@ref) 记录了在评估表达式过程中内存使用和垃圾收集的高级统计信息，但记录每个垃圾收集事件可能会很有用，以便直观地了解垃圾收集器运行的频率、每次运行的持续时间以及每次收集的垃圾量。这可以通过 [`GC.enable_logging(true)`](@ref) 来启用，这会导致 Julia 在每次发生垃圾收集时将信息记录到 stderr。

### [Allocation Profiler](@id allocation-profiler)

!!! compat "Julia 1.8"
    此功能至少需要 Julia 1.8。


分配分析器在运行时记录每个分配的堆栈跟踪、类型和大小。可以通过 [`Profile.Allocs.@profile`](@ref) 调用它。

此关于分配的信息作为 `Alloc` 对象的数组返回，封装在 `AllocResults` 对象中。当前可视化这些信息的最佳方式是使用 [PProf.jl](https://github.com/JuliaPerf/PProf.jl) 和 [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl) 包，这些包可以可视化进行最多分配的调用栈。

分配分析器确实有显著的开销，因此可以传递 `sample_rate` 参数来加快速度，方法是让它跳过一些分配。传递 `sample_rate=1.0` 将使其记录所有内容（这很慢）；`sample_rate=0.1` 将仅记录 10% 的分配（更快），等等。

!!! compat "Julia 1.11"
    旧版本的 Julia 无法在所有情况下捕获类型。在旧版本的 Julia 中，如果你看到类型为 `Profile.Allocs.UnknownType` 的分配，这意味着分析器不知道分配了什么类型的对象。这主要发生在分配来自编译器生成的代码时。有关更多信息，请参见 [issue #43688](https://github.com/JuliaLang/julia/issues/43688)。

    自 Julia 1.11 起，所有分配都应报告类型。


有关如何使用此工具的更多详细信息，请参阅以下来自JuliaCon 2022的演讲：https://www.youtube.com/watch?v=BFvpwC8hEWQ

##### Allocation Profiler Example

在这个简单的例子中，我们使用 PProf 来可视化分配配置文件。你可以使用其他可视化工具。我们收集配置文件（指定采样率），然后进行可视化。

```julia
using Profile, PProf
Profile.Allocs.clear()
Profile.Allocs.@profile sample_rate=0.0001 my_function()
PProf.Allocs.pprof()
```

这是一个更深入的示例，展示了我们如何调整采样率。一个好的目标样本数量大约在 1 - 10 千之间。样本太多，配置文件可视化工具可能会不堪重负，分析将变得缓慢。样本太少，则没有代表性样本。

```julia-repl
julia> import Profile

julia> @time my_function()  # Estimate allocations from a (second-run) of the function
  0.110018 seconds (1.50 M allocations: 58.725 MiB, 17.17% gc time)
500000

julia> Profile.Allocs.clear()

julia> Profile.Allocs.@profile sample_rate=0.001 begin   # 1.5 M * 0.001 = ~1.5K allocs.
           my_function()
       end
500000

julia> prof = Profile.Allocs.fetch();  # If you want, you can also manually inspect the results.

julia> length(prof.allocs)  # Confirm we have expected number of allocations.
1515

julia> using PProf  # Now, visualize with an external tool, like PProf or ProfileCanvas.

julia> PProf.Allocs.pprof(prof; from_c=false)  # You can optionally pass in a previously fetched profile result.
Analyzing 1515 allocation samples... 100%|████████████████████████████████| Time: 0:00:00
Main binary filename not available.
Serving web UI on http://localhost:62261
"alloc-profile.pb.gz"
```

然后您可以通过导航到 http://localhost:62261 来查看配置文件，并且配置文件已保存到磁盘。有关更多选项，请参阅 PProf 包。

##### Allocation Profiling Tips

如上所述，目标是在您的个人资料中大约有1-10千个样本。

请注意，我们是在*所有分配*的空间中均匀采样，并且没有根据分配的大小对我们的样本进行加权。因此，给定的分配配置文件可能无法代表您程序中大多数字节的分配位置，除非您设置了`sample_rate=1`。

分配可以来自用户直接构造对象，但也可以来自运行时内部或插入到编译代码中以处理类型不稳定。查看“源代码”视图可以帮助隔离它们，然后其他外部工具，例如 [`Cthulhu.jl`](https://github.com/JuliaDebug/Cthulhu.jl) 可以用于识别分配的原因。

##### Allocation Profile Visualization Tools

现在有几种分析可视化工具可以显示分配配置文件。以下是我们所知道的一些主要工具的小列表：

  * [PProf.jl](https://github.com/JuliaPerf/PProf.jl)
  * [ProfileCanvas.jl](https://github.com/pfitzseb/ProfileCanvas.jl)
  * VSCode 内置的性能分析器 (`@profview_allocs`) [需要文档]
  * 在 REPL 中直接查看结果

      * 您可以通过 [`Profile.Allocs.fetch()`](@ref) 在 REPL 中检查结果，以查看每个分配的堆栈跟踪和类型。

#### Line-by-Line Allocation Tracking

一种测量分配的替代方法是使用 `--track-allocation=<setting>` 命令行选项启动 Julia，您可以选择 `none`（默认，不测量分配）、`user`（测量除 Julia 核心代码外的所有内存分配）或 `all`（测量每行 Julia 代码的内存分配）。分配会针对每行编译后的代码进行测量。当您退出 Julia 时，累积结果会写入以 `.mem` 结尾的文本文件，这些文件位于与源文件相同的目录中。每一行列出了分配的总字节数。[`Coverage` package](https://github.com/JuliaCI/Coverage.jl) 包含一些基本的分析工具，例如按分配的字节数对行进行排序。

在解释结果时，有几个重要细节。在 `user` 设置下，直接从 REPL 调用的任何函数的第一行将由于 REPL 代码本身发生的事件而表现出分配。更重要的是，JIT 编译也会增加分配计数，因为 Julia 的编译器大部分是用 Julia 编写的（而编译通常需要内存分配）。推荐的程序是通过执行所有你想分析的命令来强制编译，然后调用 [`Profile.clear_malloc_data()`](@ref) 来重置所有分配计数器。最后，执行所需的命令并退出 Julia，以触发 `.mem` 文件的生成。

!!! note
    `--track-allocation` 改变了代码生成以记录分配，因此分配可能与没有该选项时的情况不同。我们建议使用 [allocation profiler](@ref allocation-profiler) 代替。


## External Profiling

目前，Julia 支持 `Intel VTune`、`OProfile` 和 `perf` 作为外部性能分析工具。

根据您选择的工具，在 `Make.user` 中将 `USE_INTEL_JITEVENTS`、`USE_OPROFILE_JITEVENTS` 和 `USE_PERF_JITEVENTS` 设置为 1。支持多个标志。

在运行 Julia 之前，请将环境变量 [`ENABLE_JITPROFILING`](@ref ENABLE_JITPROFILING) 设置为 1。

现在你有多种方法来使用这些工具！例如，使用 `OProfile` 你可以尝试简单的录制：

```
>ENABLE_JITPROFILING=1 sudo operf -Vdebug ./julia test/fastmath.jl
>opreport -l `which ./julia`
```

或者类似地使用 `perf`：

```
$ ENABLE_JITPROFILING=1 perf record -o /tmp/perf.data --call-graph dwarf -k 1 ./julia /test/fastmath.jl
$ perf inject --jit --input /tmp/perf.data --output /tmp/perf-jit.data
$ perf report --call-graph -G -i /tmp/perf-jit.data
```

还有许多更有趣的事情可以测量您的程序，要获取完整列表，请阅读 [Linux perf examples page](https://www.brendangregg.com/perf.html)。

请记住，perf 为每次执行保存一个 `perf.data` 文件，即使对于小程序，这个文件也可能变得相当大。此外，perf LLVM 模块会在 `~/.debug/jit` 中临时保存调试对象，请记得定期清理该文件夹。
