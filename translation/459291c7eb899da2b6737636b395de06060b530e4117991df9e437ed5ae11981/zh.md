# Initialization of the Julia runtime

Julia运行时如何执行`julia -e 'println("Hello World!")'`？

## `main()`

执行从 [`main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c) 开始，这调用了 `jl_load_repl()` 在 [`cli/loader_lib.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_lib.c) 中，这加载了一些库，最终调用了 [`jl_repl_entrypoint()` in `src/jlapi.c`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c)。

`jl_repl_entrypoint()` 调用 [`libsupport_init()`](https://github.com/JuliaLang/julia/blob/master/src/support/libsupportinit.c) 来设置 C 库的区域设置并初始化 "ios" 库（参见 [`ios_init_stdstreams()`](https://github.com/JuliaLang/julia/blob/master/src/support/ios.c) 和 [Legacy `ios.c` library](@ref Legacy-ios.c-library))。

下一个 [`jl_parse_opts()`](https://github.com/JuliaLang/julia/blob/master/src/jloptions.c) 被调用以处理命令行选项。请注意，`jl_parse_opts()` 仅处理影响代码生成或早期初始化的选项。其他选项稍后由 [`exec_options()` in `base/client.jl`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) 处理。

`jl_parse_opts()` 将命令行选项存储在 [global `jl_options` struct](https://github.com/JuliaLang/julia/blob/master/src/julia.h)。

## `julia_init()`

[`julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) 被 `main()` 调用，并调用 [`_julia_init()` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c)。

`_julia_init()` 首先调用 `libsupport_init()`，第二次调用时它不执行任何操作。

[`restore_signals()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) 被称为将信号处理程序掩码置零。

[`jl_resolve_sysimg_location()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) 搜索配置的路径以获取基础系统映像。请参见 [Building the Julia system image](@ref Building-the-Julia-system-image)。

[`jl_gc_init()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) 设置了弱引用、保留值和终结的分配池和列表。

[`jl_init_frontend()`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) 加载并初始化一个包含扫描器/解析器的预编译femtolisp映像。

[`jl_init_types()`](https://github.com/JuliaLang/julia/blob/master/src/jltypes.c) 创建 `jl_datatype_t` 类型描述对象，用于 [built-in types defined in `julia.h`](https://github.com/JuliaLang/julia/blob/master/src/julia.h)。例如。

```c
jl_any_type = jl_new_abstracttype(jl_symbol("Any"), core, NULL, jl_emptysvec);
jl_any_type->super = jl_any_type;

jl_type_type = jl_new_abstracttype(jl_symbol("Type"), core, jl_any_type, jl_emptysvec);

jl_int32_type = jl_new_primitivetype(jl_symbol("Int32"), core,
                                     jl_any_type, jl_emptysvec, 32);
```

[`jl_init_tasks()`](https://github.com/JuliaLang/julia/blob/master/src/task.c) 创建 `jl_datatype_t* jl_task_type` 对象；初始化全局 `jl_root_task` 结构；并将 `jl_current_task` 设置为根任务。

[`jl_init_codegen()`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp) 初始化 [LLVM library](https://llvm.org)。

[`jl_init_serializer()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) 初始化内置 `jl_value_t` 值的 8 位序列化标签。

如果没有 sysimg 文件 (`!jl_options.image_file`)，则会创建 `Core` 和 `Main` 模块，并评估 `boot.jl`：

`jl_core_module = jl_new_module(jl_symbol("Core"))` 创建了 Julia 的 `Core` 模块。

[`jl_init_intrinsic_functions()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) 创建了一个新的 Julia 模块 `Intrinsics`，其中包含常量 `jl_intrinsic_type` 符号。这些符号为每个 [intrinsic function](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) 定义了一个整数代码。[`emit_intrinsic()`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp) 在代码生成期间将这些符号转换为 LLVM 指令。

[`jl_init_primitives()`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c) 将 C 函数钩子连接到 Julia 函数符号。例如，符号 `Core.:(===)()` 通过调用 `add_builtin_func("===", jl_f_is)` 绑定到 C 函数指针 `jl_f_is()`。

[`jl_new_main_module()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) 创建全局 "Main" 模块并设置 `jl_current_task->current_module = jl_main_module`。

注意：`_julia_init()` [then sets](https://github.com/JuliaLang/julia/blob/master/src/init.c) `jl_root_task->current_module = jl_core_module`。此时，`jl_root_task` 是 `jl_current_task` 的别名，因此上面由 `jl_new_main_module()` 设置的 `current_module` 被覆盖。

[`jl_load("boot.jl", sizeof("boot.jl"))`](https://github.com/JuliaLang/julia/blob/master/src/init.c) 调用 [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c)，该函数重复调用 [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) 来执行 [`boot.jl`](https://github.com/JuliaLang/julia/blob/master/base/boot.jl)。<!– TODO – 深入研究 eval? –>

[`jl_get_builtin_hooks()`](https://github.com/JuliaLang/julia/blob/master/src/init.c) 初始化全局 C 指针，以指向在 `boot.jl` 中定义的 Julia 全局变量。

[`jl_init_box_caches()`](https://github.com/JuliaLang/julia/blob/master/src/datatype.c) 预分配全局装箱整数值对象，适用于值高达 1024。这加快了后续装箱整数的分配。例如：

```c
jl_value_t *jl_box_uint8(uint32_t x)
{
    return boxed_uint8_cache[(uint8_t)x];
}
```

[`_julia_init()` iterates](https://github.com/JuliaLang/julia/blob/master/src/init.c) 在 `jl_core_module->bindings.table` 上查找 `jl_datatype_t` 值，并将类型名称的模块前缀设置为 `jl_core_module`。

[`jl_add_standard_imports(jl_main_module)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) does "using Base" in the "Main" module.

注意：`_julia_init()` 现在恢复为 `jl_root_task->current_module = jl_main_module`，就像在被设置为 `jl_core_module` 之前一样。

为 `SIGSEGV`（OSX，Linux）和 `SIGFPE`（Windows）初始化特定于平台的信号处理程序。

其他信号（`SIGINFO, SIGBUS, SIGILL, SIGTERM, SIGABRT, SIGQUIT, SIGSYS` 和 `SIGPIPE`）被连接到 [`sigdie_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c)，该链接会打印回溯信息。

[`jl_init_restored_module()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) 调用 [`jl_module_run_initializer()`](https://github.com/JuliaLang/julia/blob/master/src/module.c) 对每个反序列化的模块运行 `__init__()` 函数。

最后 [`sigint_handler()`](https://github.com/JuliaLang/julia/blob/master/src/signals-unix.c) 已连接到 `SIGINT` 并调用 `jl_throw(jl_interrupt_exception)`。

`_julia_init()` 然后返回 [back to `main()` in `cli/loader_exe.c`](https://github.com/JuliaLang/julia/blob/master/cli/loader_exe.c)，而 `main()` 调用 `repl_entrypoint(argc, (char**)argv)`。

!!! sidebar "sysimg"
    如果存在 sysimg 文件，它包含了 `Core` 和 `Main` 模块的预编译镜像（以及 `boot.jl` 创建的其他内容）。请参见 [Building the Julia system image](@ref Building-the-Julia-system-image)。

    [`jl_restore_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) 将保存的 sysimg 反序列化到当前的 Julia 运行时环境中，并在下面的 `jl_init_box_caches()` 之后继续初始化...

    注意：[`jl_restore_system_image()` (and `staticdata.c` in general)](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) 使用了 [Legacy `ios.c` library](@ref Legacy-ios.c-library)。


## `repl_entrypoint()`

[`repl_entrypoint()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) 将 `argv[]` 的内容加载到 [`Base.ARGS`](@ref) 中。

如果在命令行中提供了一个 `.jl` "程序" 文件，那么 [`exec_program()`](https://github.com/JuliaLang/julia/blob/master/src/jlapi.c) 调用 [`jl_load(program,len)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)，该调用又调用 [`jl_parse_eval_all`](https://github.com/JuliaLang/julia/blob/master/src/ast.c)，然后反复调用 [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) 来执行程序。

However, in our example (`julia -e 'println("Hello World!")'`), [`jl_get_global(jl_base_module, jl_symbol("_start"))`](https://github.com/JuliaLang/julia/blob/master/src/module.c) looks up [`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) and [`jl_apply()`](https://github.com/JuliaLang/julia/blob/master/src/julia.h) executes it.

## `Base._start`

[`Base._start`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) 调用 [`Base.exec_options`](https://github.com/JuliaLang/julia/blob/master/base/client.jl)，它调用 [`jl_parse_input_line("println("Hello World!")")`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) 来创建一个表达式对象，并且 [`Core.eval(Main, ex)`](@ref Core.eval) 在 `Main` 的模块上下文中执行解析后的表达式 `ex`。

## `Core.eval`

[`Core.eval(Main, ex)`](@ref Core.eval) 调用 [`jl_toplevel_eval_in(m, ex)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)，它调用 [`jl_toplevel_eval_flex`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c)。 `jl_toplevel_eval_flex` 实现了一个简单的启发式方法来决定是编译给定的代码块还是通过解释器运行它。当给定 `println("Hello World!")` 时，它通常会决定通过解释器运行代码，在这种情况下，它调用 [`jl_interpret_toplevel_thunk`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c)，然后调用 [`eval_body`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c)。

下面的堆栈转储显示了解释器如何通过 [`Base.println()`](@ref) 和 [`Base.print()`](@ref) 的各种方法，最终到达 [`write(s::IO, a::Array{T}) where T`](https://github.com/JuliaLang/julia/blob/master/base/stream.jl)，该方法执行 `ccall(jl_uv_write())`。

[`jl_uv_write()`](https://github.com/JuliaLang/julia/blob/master/src/jl_uv.c) 调用 `uv_write()` 将 "Hello World!" 写入 `JL_STDOUT`。参见 [Libuv wrappers for stdio](@ref Libuv-wrappers-for-stdio)。

```
Hello World!
```

| Stack frame                   | Source code     | Notes                                                |
|:----------------------------- |:--------------- |:---------------------------------------------------- |
| `jl_uv_write()`               | `jl_uv.c`       | called though [`ccall`](@ref)                        |
| `julia_write_282942`          | `stream.jl`     | function `write!(s::IO, a::Array{T}) where T`        |
| `julia_print_284639`          | `ascii.jl`      | `print(io::IO, s::String) = (write(io, s); nothing)` |
| `jlcall_print_284639`         |                 |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.print(Base.TTY, String)`                       |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.print(Base.TTY, String, Char, Char...)`        |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_f_apply()`                | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.println(Base.TTY, String, String...)`          |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_trampoline()`             | `builtins.c`    |                                                      |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `jl_apply_generic()`          | `gf.c`          | `Base.println(String,)`                              |
| `jl_apply()`                  | `julia.h`       |                                                      |
| `do_call()`                   | `interpreter.c` |                                                      |
| `eval_body()`                 | `interpreter.c` |                                                      |
| `jl_interpret_toplevel_thunk` | `interpreter.c` |                                                      |
| `jl_toplevel_eval_flex`       | `toplevel.c`    |                                                      |
| `jl_toplevel_eval_in`         | `toplevel.c`    |                                                      |
| `Core.eval`                   | `boot.jl`       |                                                      |

由于我们的示例只有一个函数调用，它已经完成了打印“Hello World！”的任务，因此栈现在迅速回到 `main()`。

## `jl_atexit_hook()`

`main()` 调用 [`jl_atexit_hook()`](https://github.com/JuliaLang/julia/blob/master/src/init.c)。这调用了 `Base._atexit`，然后调用 [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c) 并清理 libuv 句柄。

## `julia_save()`

最后，`main()` 调用 [`julia_save()`](https://github.com/JuliaLang/julia/blob/master/src/init.c)，如果在命令行中请求，将运行时状态保存到新的系统映像中。请参见 [`jl_compile_all()`](https://github.com/JuliaLang/julia/blob/master/src/gf.c) 和 [`jl_save_system_image()`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c)。
