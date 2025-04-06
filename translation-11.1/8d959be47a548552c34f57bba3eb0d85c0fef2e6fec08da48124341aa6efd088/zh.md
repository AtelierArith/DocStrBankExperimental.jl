# [gdb debugging tips](@id gdb-debugging-tips)

## Displaying Julia variables

在 `gdb` 中，任何 `jl_value_t*` 对象 `obj` 可以使用以下方式显示：

```
(gdb) call jl_(obj)
```

该对象将在 `julia` 会话中显示，而不是在 gdb 会话中。这是一种有用的方法，可以发现由 Julia 的 C 代码操作的对象的类型和值。

同样，如果您正在调试 Julia 的一些内部（例如，`compiler.jl`），您可以使用以下方式打印 `obj`：

```julia
ccall(:jl_, Cvoid, (Any,), obj)
```

这是一个很好地规避由于Julia的输出流初始化顺序而产生的问题的方法。

Julia的flisp解释器使用`value_t`对象；这些可以通过`call fl_print(fl_ctx, ios_stdout, obj)`进行显示。

## Useful Julia variables for Inspecting

虽然许多变量的地址，例如单例，对于许多故障的打印是有用的，但还有一些额外的变量（请参见 `julia.h` 以获取完整列表）更为有用。

  * （在 `jl_apply_generic` 中）`mfunc` 和 `jl_uncompress_ast(mfunc->def, mfunc->code)` :: 用于了解调用栈的一些信息
  * `jl_lineno` 和 `jl_filename` :: 用于确定从测试中的哪一行开始调试（或确定文件解析到哪一部分）。
  * `$1` :: 并不是真正的变量，但仍然是一个有用的简写，用于引用上一个 gdb 命令的结果（例如 `print`）
  * `jl_options` :: 有时很有用，因为它列出了所有成功解析的命令行选项
  * `jl_uv_stderr` :: 因为谁不喜欢能够与标准输入输出进行交互

## Useful Julia functions for Inspecting those variables

  * `jl_print_task_backtraces(0)` :: 类似于 gdb 的 `thread apply all bt` 或 lldb 的 `thread backtrace all`。运行所有线程，同时打印所有现有任务的回溯。
  * `jl_gdblookup($pc)` :: 用于查找当前函数和行。
  * `jl_gdblookupinfo($pc)` :: 用于查找当前方法实例对象。
  * `jl_gdbdumpcode(mi)` :: 用于在 REPL 无法正常工作时转储所有的 `code_typed/code_llvm/code_asm`。
  * `jlbacktrace()` :: 用于将当前的 Julia 回溯栈转储到 stderr。仅在调用 `record_backtrace()` 之后可用。
  * `jl_dump_llvm_value(Value*)` :: 用于在 gdb 中调用 `Value->dump()`，因为它在原生环境中无法工作。例如，`f->linfo->functionObject`，`f->linfo->specFunctionObject`，以及 `to_function(f->linfo)`。
  * `jl_dump_llvm_module(Module*)` :: 用于在 gdb 中调用 `Module->dump()`，因为它在原生环境中无法工作。
  * `Type->dump()` :: 仅在 lldb 中有效。注意：添加类似 `;1` 的内容以防止 lldb 在输出上打印其提示符。
  * `jl_eval_string("expr")` :: 用于调用副作用以修改当前状态或查找符号
  * `jl_typeof(jl_value_t*)` :: 用于提取 Julia 值的类型标签（在 gdb 中，首先调用 `macro define jl_typeof jl_typeof`，或者为第一个参数选择一个简短的名称，如 `ty` 来定义一个简写）

## Inserting breakpoints for inspection from gdb

在你的 `gdb` 会话中，像这样在 `jl_breakpoint` 设置一个断点：

```
(gdb) break jl_breakpoint
```

然后在你的 Julia 代码中，通过添加调用 `jl_breakpoint` 来插入一个断点。

```julia
ccall(:jl_breakpoint, Cvoid, (Any,), obj)
```

在断点中，`obj` 可以是您希望访问的任何变量或元组。

特别有助于备份到 `jl_apply` 框架，从中可以使用例如显示函数的参数，

```
(gdb) call jl_(args[0])
```

另一个有用的框架是 `to_function(jl_method_instance_t *li, bool cstyle)`。`jl_method_instance_t*` 参数是一个结构体，包含对发送到编译器的最终 AST 的引用。然而，此时的 AST 通常会被压缩；要查看 AST，请调用 `jl_uncompress_ast`，然后将结果传递给 `jl_`：

```
#2  0x00007ffff7928bf7 in to_function (li=0x2812060, cstyle=false) at codegen.cpp:584
584          abort();
(gdb) p jl_(jl_uncompress_ast(li, li->ast))
```

## Inserting breakpoints upon certain conditions

### Loading a particular file

假设文件名为 `sysimg.jl`：

```
(gdb) break jl_load if strcmp(fname, "sysimg.jl")==0
```

### Calling a particular method

```
(gdb) break jl_apply_generic if strcmp((char*)(jl_symbol_name)(jl_gf_mtable(F)->name), "method_to_break")==0
```

由于这个函数在每次调用时都会使用，如果你这样做，所有操作将会变得慢1000倍。

## Dealing with signals

Julia 需要一些信号才能正常工作。分析器使用 `SIGUSR2` 进行采样，垃圾收集器使用 `SIGSEGV` 进行线程同步。如果您正在调试一些使用分析器或多个线程的代码，您可能希望让调试器忽略这些信号，因为它们在正常操作期间可能会非常频繁地触发。在 GDB 中执行此操作的命令是（将 `SIGSEGV` 替换为 `SIGUSR2` 或其他您想要忽略的信号）：

```
(gdb) handle SIGSEGV noprint nostop pass
```

相应的 LLDB 命令是（在进程启动后）：

```
(lldb) pro hand -p true -s false -n false SIGSEGV
```

如果您正在调试带有线程代码的段错误，可以在 `jl_critical_error` 上设置断点（`sigdie_handler` 在 Linux 和 BSD 上也应该有效），以便仅捕获实际的段错误，而不是 GC 同步点。

## Debugging during Julia's build process (bootstrap)

在 `make` 过程中发生的错误需要特别处理。Julia 是分两个阶段构建的，构建 `sys0` 和 `sys.ji`。要查看在失败时正在运行的命令，请使用 `make VERBOSE=1`。

在撰写本文时，您可以通过以下方式从 `base` 目录调试 `sys0` 阶段的构建错误：

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys0 sysimg.jl
```

您可能需要删除 `usr/lib/julia/` 中的所有文件才能使其正常工作。

您可以使用以下命令调试 `sys.ji` 阶段：

```
julia/base$ gdb --args ../usr/bin/julia-debug -C native --build ../usr/lib/julia/sys -J ../usr/lib/julia/sys0.ji sysimg.jl
```

默认情况下，任何错误都会导致 Julia 退出，即使在 gdb 下也是如此。要“现场”捕获错误，请在 `jl_error` 设置一个断点（还有其他几个有用的位置，针对特定类型的失败，包括：`jl_too_few_args`、`jl_too_many_args` 和 `jl_throw`）。

一旦捕获到错误，一个有用的技巧是沿着调用栈向上走，通过检查与 `jl_apply` 相关的调用来检查函数。以下是一个现实世界的例子：

```
Breakpoint 1, jl_throw (e=0x7ffdf42de400) at task.c:802
802 {
(gdb) p jl_(e)
ErrorException("auto_unbox: unable to determine argument type")
$2 = void
(gdb) bt 10
#0  jl_throw (e=0x7ffdf42de400) at task.c:802
#1  0x00007ffff65412fe in jl_error (str=0x7ffde56be000 <_j_str267> "auto_unbox:
   unable to determine argument type")
   at builtins.c:39
#2  0x00007ffde56bd01a in julia_convert_16886 ()
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
...
```

最近的 `jl_apply` 在帧 #3，因此我们可以回到那里查看函数 `julia_convert_16886` 的 AST。这是 `convert` 的某个方法的唯一名称。此帧中的 `f` 是一个 `jl_function_t*`，因此我们可以查看 `specTypes` 字段中的类型签名（如果有的话）：

```
(gdb) f 3
#3  0x00007ffff6541154 in jl_apply (f=0x7ffdf367f630, args=0x7fffffffc2b0, nargs=2) at julia.h:1281
1281            return f->fptr((jl_value_t*)f, args, nargs);
(gdb) p f->linfo->specTypes
$4 = (jl_tupletype_t *) 0x7ffdf39b1030
(gdb) p jl_( f->linfo->specTypes )
Tuple{Type{Float32}, Float64}           # <-- type signature for julia_convert_16886
```

然后，我们可以查看这个函数的 AST：

```
(gdb) p jl_( jl_uncompress_ast(f->linfo, f->linfo->ast) )
Expr(:lambda, Array{Any, 1}[:#s29, :x], Array{Any, 1}[Array{Any, 1}[], Array{Any, 1}[Array{Any, 1}[:#s29, :Any, 0], Array{Any, 1}[:x, :Any, 0]], Array{Any, 1}[], 0], Expr(:body,
Expr(:line, 90, :float.jl)::Any,
Expr(:return, Expr(:call, :box, :Float32, Expr(:call, :fptrunc, :Float32, :x)::Any)::Any)::Any)::Any)::Any
```

最后，也许最有用的是，我们可以强制函数重新编译，以便逐步查看代码生成过程。为此，从 `jl_lamdbda_info_t*` 中清除缓存的 `functionObject`：

```
(gdb) p f->linfo->functionObject
$8 = (void *) 0x1289d070
(gdb) set f->linfo->functionObject = NULL
```

然后，在某个有用的地方设置一个断点（例如 `emit_function`、`emit_expr`、`emit_call` 等），并运行代码生成：

```
(gdb) p jl_compile(f)
... # your breakpoint here
```

## Debugging precompilation errors

模块预编译会生成一个单独的 Julia 进程来预编译每个模块。设置断点或捕获预编译工作进程中的失败需要将调试器附加到该工作进程。最简单的方法是设置调试器监视与给定名称匹配的新进程启动。例如：

```
(gdb) attach -w -n julia-debug
```

或：

```
(lldb) process attach -w -n julia-debug
```

然后运行一个脚本/命令以开始预编译。如前所述，在父进程中使用条件断点来捕获特定的文件加载事件并缩小调试窗口。（某些操作系统可能需要替代方法，例如跟踪每个来自父进程的 `fork`）

## Mozilla's Record and Replay Framework (rr)

Julia 现在可以直接使用 [rr](https://rr-project.org/)，这是 Mozilla 的轻量级录制和确定性调试框架。这使您能够以确定性的方式重放执行的跟踪。重放的执行的地址空间、寄存器内容、系统调用数据等在每次运行中都是完全相同的。

需要最新版本的 rr（3.1.0 或更高版本）。

### Reproducing concurrency bugs with rr

rr 默认模拟单线程机器。为了调试并发代码，您可以使用 `rr record --chaos`，这将使 rr 随机模拟一到八个核心。因此，您可能想要设置 `JULIA_NUM_THREADS=8` 并在 rr 下重新运行您的代码，直到捕获到错误。
