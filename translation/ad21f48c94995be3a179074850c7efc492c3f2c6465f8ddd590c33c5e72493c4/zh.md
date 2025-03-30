```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Logging/docs/src/index.md"
```

# [Logging](@id man-logging)

[`Logging`](@ref Logging.Logging) 模块提供了一种记录计算历史和进展的方法，作为事件日志。事件是通过在源代码中插入日志语句来创建的，例如：

```julia
@warn "Abandon printf debugging, all ye who enter here!"
┌ Warning: Abandon printf debugging, all ye who enter here!
└ @ Main REPL[1]:1
```

系统提供了几个优于在源代码中到处调用 `println()` 的优势。首先，它允许您控制消息的可见性和呈现方式，而无需编辑源代码。例如，与上面的 `@warn` 相比

```julia
@debug "The sum of some values $(sum(rand(100)))"
```

默认情况下不会产生任何输出。此外，像这样的调试语句留在源代码中是非常便宜的，因为系统会避免评估消息，如果它后来会被忽略。在这种情况下，`sum(rand(100))` 和相关的字符串处理将永远不会被执行，除非启用调试日志记录。

其次，日志工具允许您将任意数据作为一组键值对附加到每个事件上。这使您能够捕获局部变量和其他程序状态以供后续分析。例如，要将局部数组变量 `A` 和向量 `v` 的和作为键 `s` 附加，您可以使用

```jldoctest
A = ones(Int, 4, 4)
v = ones(100)
@info "Some variables"  A  s=sum(v)

# output
┌ Info: Some variables
│   A =
│    4×4 Matrix{Int64}:
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
│     1  1  1  1
└   s = 100.0
```

所有的日志宏 `@debug`、`@info`、`@warn` 和 `@error` 共享一些共同特性，这些特性在更通用的宏 [`@logmsg`](@ref) 的文档中有详细描述。

## Log event structure

每个事件生成多个数据项，其中一些由用户提供，另一些则是自动提取的。我们先来看看用户定义的数据：

  * *日志级别* 是用于早期过滤的消息的广泛类别。 有几种标准级别，类型为 [`LogLevel`](@ref)；用户定义的级别也是可能的。 每个级别在目的上都是不同的：

      * [`Logging.Debug`](@ref)（日志级别 -1000）是针对程序开发者的信息。这些事件默认是禁用的。
      * [`Logging.Info`](@ref)（日志级别 0）用于向用户提供一般信息。可以将其视为直接使用 `println` 的替代方案。
      * [`Logging.Warn`](@ref)（日志级别 1000）意味着出现了问题，可能需要采取行动，但目前程序仍在正常运行。
      * [`Logging.Error`](@ref)（日志级别 2000）意味着出现了问题，并且不太可能被恢复，至少在这部分代码中。通常，这个日志级别是不必要的，因为抛出异常可以传达所有所需的信息。
  * *消息* 是描述事件的对象。根据约定，作为消息传递的 `AbstractString` 被假定为 markdown 格式。其他类型将使用 `print(io, obj)` 或 `string(obj)` 进行文本输出，并可能使用 `show(io,mime,obj)` 进行安装的日志记录器中使用的其他多媒体显示。
  * 可选的 *键–值对* 允许将任意数据附加到每个事件上。一些键具有传统意义，可能会影响事件的解释方式（请参见 [`@logmsg`](@ref)）。

系统还为每个事件生成一些标准信息：

  * 扩展日志宏的 `module`。
  * 在源代码中记录宏发生的 `file` 和 `line`。
  * 一个消息 `id` 是一个唯一的、固定的标识符，用于标识日志宏出现的 *源代码语句*。这个标识符的设计旨在保持相对稳定，即使文件的源代码发生变化，只要日志语句本身保持不变。
  * 一个 `group` 用于事件，默认设置为文件的基本名称，不带扩展名。 这可以用于将消息更细致地分组到类别中，而不仅仅是日志级别（例如，所有弃用警告都有组 `:depwarn`），或者在模块之间或内部进行逻辑分组。

请注意，某些有用的信息，例如事件时间，默认情况下并未包含。这是因为提取此类信息可能代价高昂，并且对于当前记录器来说也是*动态*可用的。定义一个 [custom logger](@ref AbstractLogger-interface) 来根据需要增强事件数据，包括时间、回溯、全局变量的值和其他有用信息是很简单的。

## Processing log events

正如您在示例中所看到的，日志语句并未提及日志事件的去向或处理方式。这是一个关键的设计特性，使系统具有可组合性，并且适合并发使用。它通过分离两个不同的关注点来实现这一点：

  * *创建* 日志事件是模块作者的责任，他们需要决定事件触发的位置以及包含哪些信息。
  * *处理*日志事件——即显示、过滤、聚合和记录——是应用程序作者的关注点，他们需要将多个模块整合成一个协作的应用程序。

### Loggers

事件的处理由一个 *logger* 执行，它是第一个可配置的用户代码，用于查看事件。所有的日志记录器必须是 [`AbstractLogger`](@ref) 的子类型。

当事件被触发时，通过查找任务本地的记录器并以全局记录器作为后备，找到合适的记录器。这里的想法是应用程序代码知道日志事件应该如何处理，并且存在于调用栈的顶部。因此，我们应该向上查找调用栈以发现记录器——也就是说，记录器应该是*动态作用域*的。（这与记录框架的一个对比点是，记录器是*词法作用域*的；由模块作者显式提供或作为简单的全局变量。在这样的系统中，在组合多个模块的功能时控制日志记录是很尴尬的。）

全局记录器可以通过 [`global_logger`](@ref) 设置，任务本地记录器可以通过 [`with_logger`](@ref) 控制。新生成的任务会继承父任务的记录器。

库提供了三种记录器类型。 [`ConsoleLogger`](@ref) 是您在启动 REPL 时看到的默认记录器。它以可读的文本格式显示事件，并尝试提供简单但用户友好的格式化和过滤控制。 [`NullLogger`](@ref) 是一种方便的方式，可以在必要时丢弃所有消息；它是 [`devnull`](@ref) 流的记录等价物。 [`SimpleLogger`](@ref) 是一种非常简单的文本格式化记录器，主要用于调试记录系统本身。

自定义日志记录器应提供对[reference section](@ref AbstractLogger-interface)中描述的函数的重载。

### Early filtering and message handling

当事件发生时，会进行一些早期过滤步骤，以避免生成将被丢弃的消息：

1. 消息日志级别会与全局最低级别进行检查（通过 [`disable_logging`](@ref) 设置）。这是一个粗糙但极其便宜的全局设置。
2. 当前的日志记录器状态被查找，并且消息级别与日志记录器缓存的最小级别进行检查，这可以通过调用 [`Logging.min_enabled_level`](@ref) 来实现。此行为可以通过环境变量进行覆盖（稍后会详细介绍）。
3. [`Logging.shouldlog`](@ref) 函数被当前日志记录器调用，接受一些最小的信息（级别、模块、组、id），这些信息可以静态计算。最有用的是，`shouldlog` 被传递一个事件 `id`，可以用来根据缓存的谓词提前丢弃事件。

如果所有这些检查都通过，消息和键值对将被完全评估并通过 [`Logging.handle_message`](@ref) 函数传递给当前的记录器。`handle_message()` 可能会根据需要执行额外的过滤，并将事件显示在屏幕上，保存到文件等。

在生成日志事件时发生的异常会被默认捕获并记录。这可以防止单个损坏的事件导致应用程序崩溃，这在生产系统中启用不常用的调试事件时非常有用。此行为可以通过扩展 [`Logging.catch_exceptions`](@ref) 来根据日志记录器类型进行自定义。

## Testing log events

日志事件是运行正常代码的副作用，但您可能会发现自己想要测试特定的信息消息和警告。`Test`模块提供了一个[`@test_logs`](@ref)宏，可以用于对日志事件流进行模式匹配。

## Environment variables

消息过滤可以通过 [`JULIA_DEBUG`](@ref JULIA_DEBUG) 环境变量进行影响，并作为一种简单的方法来为文件或模块启用调试日志。使用 `JULIA_DEBUG=loading` 加载 julia 将激活 `loading.jl` 中的 `@debug` 日志消息。例如，在 Linux shell 中：

```
$ JULIA_DEBUG=loading julia -e 'using OhMyREPL'
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
[ Info: Recompiling stale cache file /home/user/.julia/compiled/v0.7/OhMyREPL.ji for module OhMyREPL
┌ Debug: Rejecting cache file /home/user/.julia/compiled/v0.7/Tokenize.ji due to it containing an incompatible cache header
└ @ Base loading.jl:1328
...
```

在 Windows 上，可以通过首先在 `CMD` 中运行 `set JULIA_DEBUG="loading"`，以及在 `Powershell` 中运行 `$env:JULIA_DEBUG="loading"` 来实现相同的效果。

同样，环境变量可以用来启用模块的调试日志记录，例如 `Pkg`，或模块根（参见 [`Base.moduleroot`](@ref)）。要启用所有调试日志记录，请使用特殊值 `all`。

要从 REPL 中启用调试日志，请将 `ENV["JULIA_DEBUG"]` 设置为感兴趣的模块名称。在 REPL 中定义的函数属于模块 `Main`；可以通过以下方式启用它们的日志记录：

```julia-repl
julia> foo() = @debug "foo"
foo (generic function with 1 method)

julia> foo()

julia> ENV["JULIA_DEBUG"] = Main
Main

julia> foo()
┌ Debug: foo
└ @ Main REPL[1]:1

```

使用逗号分隔符启用多个模块的调试：`JULIA_DEBUG=loading,Main`。

## Examples

### Example: Writing log events to a file

有时将日志事件写入文件是有用的。以下是如何使用任务本地和全局记录器将信息写入文本文件的示例：

```julia-repl
# Load the logging module
julia> using Logging

# Open a textfile for writing
julia> io = open("log.txt", "w+")
IOStream(<file log.txt>)

# Create a simple logger
julia> logger = SimpleLogger(io)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# Log a task-specific message
julia> with_logger(logger) do
           @info("a context specific log message")
       end

# Write all buffered messages to the file
julia> flush(io)

# Set the global logger to logger
julia> global_logger(logger)
SimpleLogger(IOStream(<file log.txt>), Info, Dict{Any,Int64}())

# This message will now also be written to the file
julia> @info("a global log message")

# Close the file
julia> close(io)
```

### Example: Enable debug-level messages

这是一个创建 [`ConsoleLogger`](@ref) 的示例，它允许通过任何日志级别高于或等于 [`Logging.Debug`](@ref) 的消息。

```julia-repl
julia> using Logging

# Create a ConsoleLogger that prints any log messages with level >= Debug to stderr
julia> debuglogger = ConsoleLogger(stderr, Logging.Debug)

# Enable debuglogger for a task
julia> with_logger(debuglogger) do
           @debug "a context specific log message"
       end

# Set the global logger
julia> global_logger(debuglogger)
```

## Reference

### Logging module

```@docs
Logging.Logging
```

### Creating events

```@docs
Logging.@logmsg
Logging.LogLevel
Logging.Debug
Logging.Info
Logging.Warn
Logging.Error
Logging.BelowMinLevel
Logging.AboveMaxLevel
```

### [Processing events with AbstractLogger](@id AbstractLogger-interface)

事件处理是通过重写与 `AbstractLogger` 相关的函数来控制的：

| Methods to implement                |                        | Brief description                            |
|:----------------------------------- |:---------------------- |:-------------------------------------------- |
| [`Logging.handle_message`](@ref)    |                        | Handle a log event                           |
| [`Logging.shouldlog`](@ref)         |                        | Early filtering of events                    |
| [`Logging.min_enabled_level`](@ref) |                        | Lower bound for log level of accepted events |
| **Optional methods**                | **Default definition** | **Brief description**                        |
| [`Logging.catch_exceptions`](@ref)  | `true`                 | Catch exceptions during event evaluation     |

```@docs
Logging.AbstractLogger
Logging.handle_message
Logging.shouldlog
Logging.min_enabled_level
Logging.catch_exceptions
Logging.disable_logging
```

### Using Loggers

Logger 安装和检查：

```@docs
Logging.global_logger
Logging.with_logger
Logging.current_logger
```

系统提供的日志记录器：

```@docs
Logging.NullLogger
Logging.ConsoleLogger
Logging.SimpleLogger
```
