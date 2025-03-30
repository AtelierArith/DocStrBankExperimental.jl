# Stack Traces

`StackTraces` 模块提供了简单的堆栈跟踪，既易于人类阅读，又易于程序化使用。

## Viewing a stack trace

获取堆栈跟踪的主要函数是 [`stacktrace`](@ref)：

```julia-repl
6-element Array{Base.StackTraces.StackFrame,1}:
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

调用 [`stacktrace()`](@ref) 返回一个 [`StackTraces.StackFrame`](@ref) 的向量。为了方便使用，可以用别名 [`StackTraces.StackTrace`](@ref) 替代 `Vector{StackFrame}`。 （带有 `[...]` 的示例表示输出可能会根据代码的运行方式而有所不同。）

```julia-repl
julia> example() = stacktrace()
example (generic function with 1 method)

julia> example()
7-element Array{Base.StackTraces.StackFrame,1}:
 example() at REPL[1]:1
 top-level scope
 eval at boot.jl:317 [inlined]
[...]

julia> @noinline child() = stacktrace()
child (generic function with 1 method)

julia> @noinline parent() = child()
parent (generic function with 1 method)

julia> grandparent() = parent()
grandparent (generic function with 1 method)

julia> grandparent()
9-element Array{Base.StackTraces.StackFrame,1}:
 child() at REPL[3]:1
 parent() at REPL[4]:1
 grandparent() at REPL[5]:1
[...]
```

注意，当调用 [`stacktrace()`](@ref) 时，您通常会看到一个带有 `eval at boot.jl` 的帧。当从 REPL 调用 `4d61726b646f776e2e436f64652822222c2022737461636b747261636528292229_40726566` 时，您还会在堆栈中看到一些来自 `REPL.jl` 的额外帧，通常看起来像这样：

```julia-repl
julia> example() = stacktrace()
example (generic function with 1 method)

julia> example()
7-element Array{Base.StackTraces.StackFrame,1}:
 example() at REPL[1]:1
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

## Extracting useful information

每个 [`StackTraces.StackFrame`](@ref) 包含函数名称、文件名称、行号、lambda 信息、一个指示帧是否被内联的标志、一个指示它是否是 C 函数的标志（默认情况下 C 函数不会出现在堆栈跟踪中），以及 [`backtrace`](@ref) 返回的指针的整数表示。

```julia-repl
julia> frame = stacktrace()[3]
eval(::Module, ::Expr) at REPL.jl:5

julia> frame.func
:eval

julia> frame.file
Symbol("~/julia/usr/share/julia/stdlib/v0.7/REPL/src/REPL.jl")

julia> frame.line
5

julia> frame.linfo
MethodInstance for eval(::Module, ::Expr)

julia> frame.inlined
false

julia> frame.from_c
false

julia> frame.pointer
0x00007f92d6293171
```

这使得堆栈跟踪信息可以通过编程方式获取，以便进行日志记录、错误处理等。

## Error handling

虽然在许多地方轻松访问关于调用栈当前状态的信息是有帮助的，但最明显的应用是在错误处理和调试中。

```julia-repl
julia> @noinline bad_function() = undeclared_variable
bad_function (generic function with 1 method)

julia> @noinline example() = try
           bad_function()
       catch
           stacktrace()
       end
example (generic function with 1 method)

julia> example()
7-element Array{Base.StackTraces.StackFrame,1}:
 example() at REPL[2]:4
 top-level scope
 eval at boot.jl:317 [inlined]
[...]
```

您可能会注意到，在上面的示例中，第一个堆栈帧指向第4行，其中调用了 [`stacktrace`](@ref)，而不是第2行，其中调用了 *bad_function*，并且 `bad_function` 的帧完全缺失。这是可以理解的，因为 `4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566` 是在 *catch* 的上下文中调用的。虽然在这个例子中相对容易找到错误的实际来源，但在复杂情况下，追踪错误的来源变得不那么简单。

这可以通过将 [`catch_backtrace`](@ref) 的结果传递给 [`stacktrace`](@ref) 来解决。`4d61726b646f776e2e436f64652822222c202263617463685f6261636b74726163652229_40726566` 不返回当前上下文的调用栈信息，而是返回最近异常的上下文的栈信息：

```julia-repl
julia> @noinline bad_function() = undeclared_variable
bad_function (generic function with 1 method)

julia> @noinline example() = try
           bad_function()
       catch
           stacktrace(catch_backtrace())
       end
example (generic function with 1 method)

julia> example()
8-element Array{Base.StackTraces.StackFrame,1}:
 bad_function() at REPL[1]:1
 example() at REPL[2]:2
[...]
```

注意到堆栈跟踪现在指示了适当的行号和缺失的帧。

```julia-repl
julia> @noinline child() = error("Whoops!")
child (generic function with 1 method)

julia> @noinline parent() = child()
parent (generic function with 1 method)

julia> @noinline function grandparent()
           try
               parent()
           catch err
               println("ERROR: ", err.msg)
               stacktrace(catch_backtrace())
           end
       end
grandparent (generic function with 1 method)

julia> grandparent()
ERROR: Whoops!
10-element Array{Base.StackTraces.StackFrame,1}:
 error at error.jl:33 [inlined]
 child() at REPL[1]:1
 parent() at REPL[2]:1
 grandparent() at REPL[3]:3
[...]
```

## Exception stacks and [`current_exceptions`](@ref)

!!! compat "Julia 1.1"
    异常堆栈至少需要 Julia 1.1。


在处理异常时，可能会抛出进一步的异常。检查所有这些异常以识别问题的根本原因可能是有用的。Julia 运行时通过在发生时将每个异常推送到内部 *异常堆栈* 来支持这一点。当代码正常退出 `catch` 时，任何在相关 `try` 中推送到堆栈的异常都被视为已成功处理，并从堆栈中移除。

当前异常的堆栈可以通过 [`current_exceptions`](@ref) 函数访问。例如，

```julia-repl
julia> try
           error("(A) The root cause")
       catch
           try
               error("(B) An exception while handling the exception")
           catch
               for (exc, bt) in current_exceptions()
                   showerror(stdout, exc, bt)
                   println(stdout)
               end
           end
       end
(A) The root cause
Stacktrace:
 [1] error(::String) at error.jl:33
 [2] top-level scope at REPL[7]:2
 [3] eval(::Module, ::Any) at boot.jl:319
 [4] eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 [5] macro expansion at REPL.jl:117 [inlined]
 [6] (::getfield(REPL, Symbol("##26#27")){REPL.REPLBackend})() at task.jl:259
(B) An exception while handling the exception
Stacktrace:
 [1] error(::String) at error.jl:33
 [2] top-level scope at REPL[7]:5
 [3] eval(::Module, ::Any) at boot.jl:319
 [4] eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 [5] macro expansion at REPL.jl:117 [inlined]
 [6] (::getfield(REPL, Symbol("##26#27")){REPL.REPLBackend})() at task.jl:259
```

在这个例子中，根本原因异常（A）首先出现在堆栈上，后面跟着另一个异常（B）。在正常退出两个捕获块后（即，没有抛出进一步的异常），所有异常都从堆栈中移除，并且不再可访问。

异常堆栈存储在发生异常的 `Task` 上。当一个任务因未捕获的异常而失败时，可以使用 `current_exceptions(task)` 来检查该任务的异常堆栈。

## Comparison with [`backtrace`](@ref)

对 [`backtrace`](@ref) 的调用返回一个 `Union{Ptr{Nothing}, Base.InterpreterIP}` 的向量，然后可以将其传递给 [`stacktrace`](@ref) 进行翻译：

```julia-repl
julia> trace = backtrace()
18-element Array{Union{Ptr{Nothing}, Base.InterpreterIP},1}:
 Ptr{Nothing} @0x00007fd8734c6209
 Ptr{Nothing} @0x00007fd87362b342
 Ptr{Nothing} @0x00007fd87362c136
 Ptr{Nothing} @0x00007fd87362c986
 Ptr{Nothing} @0x00007fd87362d089
 Base.InterpreterIP(CodeInfo(:(begin
      Core.SSAValue(0) = backtrace()
      trace = Core.SSAValue(0)
      return Core.SSAValue(0)
  end)), 0x0000000000000000)
 Ptr{Nothing} @0x00007fd87362e4cf
[...]

julia> stacktrace(trace)
6-element Array{Base.StackTraces.StackFrame,1}:
 top-level scope
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
```

注意到 [`backtrace`](@ref) 返回的向量有 18 个元素，而 [`stacktrace`](@ref) 返回的向量只有 6 个。这是因为默认情况下，`4d61726b646f776e2e436f64652822222c2022737461636b74726163652229_40726566` 会从堆栈中移除任何低级 C 函数。如果你想包含来自 C 调用的堆栈帧，可以这样做：

```julia-repl
julia> stacktrace(trace, true)
21-element Array{Base.StackTraces.StackFrame,1}:
 jl_apply_generic at gf.c:2167
 do_call at interpreter.c:324
 eval_value at interpreter.c:416
 eval_body at interpreter.c:559
 jl_interpret_toplevel_thunk_callback at interpreter.c:798
 top-level scope
 jl_interpret_toplevel_thunk at interpreter.c:807
 jl_toplevel_eval_flex at toplevel.c:856
 jl_toplevel_eval_in at builtins.c:624
 eval at boot.jl:317 [inlined]
 eval(::Module, ::Expr) at REPL.jl:5
 jl_apply_generic at gf.c:2167
 eval_user_input(::Any, ::REPL.REPLBackend) at REPL.jl:85
 jl_apply_generic at gf.c:2167
 macro expansion at REPL.jl:116 [inlined]
 (::getfield(REPL, Symbol("##28#29")){REPL.REPLBackend})() at event.jl:92
 jl_fptr_trampoline at gf.c:1838
 jl_apply_generic at gf.c:2167
 jl_apply at julia.h:1540 [inlined]
 start_task at task.c:268
 ip:0xffffffffffffffff
```

个别指针由 [`backtrace`](@ref) 返回，可以通过将它们传递到 [`StackTraces.StackFrame`](@ref) 来翻译成 [`StackTraces.lookup`](@ref)：

```julia-repl
julia> pointer = backtrace()[1];

julia> frame = StackTraces.lookup(pointer)
1-element Array{Base.StackTraces.StackFrame,1}:
 jl_apply_generic at gf.c:2167

julia> println("The top frame is from $(frame[1].func)!")
The top frame is from jl_apply_generic!
```
