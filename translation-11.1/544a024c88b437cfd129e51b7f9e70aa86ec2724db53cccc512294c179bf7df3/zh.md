# Eval of Julia code

学习Julia语言如何运行代码最困难的部分之一是了解所有组件如何协同工作以执行一段代码。

每段代码通常会经过许多步骤，这些步骤可能有不熟悉的名称，例如（无特定顺序）：flisp、AST、C++、LLVM、`eval`、`typeinf`、`macroexpand`、sysimg（或系统映像）、引导、编译、解析、执行、JIT、解释、装箱、拆箱、内在函数和原始函数，然后才会变成期望的结果（希望如此）。

!!! sidebar "Definitions"
      * REPL

        REPL代表读取-评估-打印循环。这就是我们对命令行环境的简短称呼。
      * AST

        抽象语法树 AST 是代码结构的数字表示。在这种形式下，代码已经被标记为有意义的，因此更适合于操作和执行。


![编译器流程图](./img/compiler_diagram.png)

## Julia Execution

整个过程的10,000英尺视图如下：

1. 用户启动 `julia`。
2. C 函数 `main()` 从 `cli/loader_exe.c` 被调用。该函数处理命令行参数，填充 `jl_options` 结构并设置变量 `ARGS`。然后它通过调用 [`julia_init` in `init.c`](https://github.com/JuliaLang/julia/blob/master/src/init.c) 来初始化 Julia，这可能会加载一个先前编译的 [sysimg](@ref dev-sysimg)。最后，它通过调用 [`Base._start()`](https://github.com/JuliaLang/julia/blob/master/base/client.jl) 将控制权交给 Julia。
3. 当 `_start()` 接管控制时，后续的命令序列取决于给定的命令行参数。例如，如果提供了文件名，它将继续执行该文件。否则，它将启动一个交互式 REPL。
4. 跳过关于 REPL 如何与用户交互的细节，我们只需说程序最终得到了一段它想要运行的代码块。
5. 如果要运行的代码块在文件中，[`jl_load(char *filename)`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) 被调用以加载文件，并且 [parse](@ref dev-parsing) 也被调用。然后每个代码片段都被传递给 `eval` 以执行。
6. 每个代码片段（或 AST）都被交给 [`eval()`](@ref) 以生成结果。
7. [`eval()`](@ref) 将每个代码片段提取并尝试在 [`jl_toplevel_eval_flex()`](https://github.com/JuliaLang/julia/blob/master/src/toplevel.c) 中运行。
8. `jl_toplevel_eval_flex()` 决定代码是否为“顶层”操作（例如 `using` 或 `module`），这在函数内部是无效的。如果是，它会将代码传递给顶层解释器。
9. `jl_toplevel_eval_flex()` 然后 [expands](@ref dev-macro-expansion) 这段代码用于消除任何宏，并将 AST "降低" 以简化执行。
10. `jl_toplevel_eval_flex()` 然后使用一些简单的启发式方法来决定是 JIT 编译 AST 还是直接解释它。
11. 大部分代码解释的工作由 [`eval` in `interpreter.c`](https://github.com/JuliaLang/julia/blob/master/src/interpreter.c) 处理。
12. 如果代码被编译，大部分工作由 `codegen.cpp` 处理。每当一个 Julia 函数第一次以给定的参数类型被调用时，[type inference](@ref dev-type-inference) 将在该函数上运行。这些信息被 [codegen](@ref dev-codegen) 步骤用来生成更快的代码。
13. 最终，用户退出 REPL，或者程序结束，`_start()` 方法返回。
14. 在退出之前，`main()` 调用 [`jl_atexit_hook(exit_code)`](https://github.com/JuliaLang/julia/blob/master/src/init.c)。这会调用 `Base._atexit()`（它会调用在 Julia 中注册的任何函数 [`atexit()`](@ref)）。然后它调用 [`jl_gc_run_all_finalizers()`](https://github.com/JuliaLang/julia/blob/master/src/gc.c)。最后，它优雅地清理所有 `libuv` 句柄，并等待它们刷新和关闭。

## [Parsing](@id dev-parsing)

Julia 解析器是一个用 femtolisp 编写的小型 lisp 程序，其源代码分布在 Julia 内部，位于 [src/flisp](https://github.com/JuliaLang/julia/tree/master/src/flisp)。

该接口的功能主要在 [`jlfrontend.scm`](https://github.com/JuliaLang/julia/blob/master/src/jlfrontend.scm) 中定义。代码 [`ast.c`](https://github.com/JuliaLang/julia/blob/master/src/ast.c) 处理了 Julia 端的这个交接。

在这个阶段，其他相关文件是 [`julia-parser.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-parser.scm)，它处理将 Julia 代码进行标记化并转换为 AST，以及 [`julia-syntax.scm`](https://github.com/JuliaLang/julia/blob/master/src/julia-syntax.scm)，它处理将复杂的 AST 表示转换为更简单的“降低”AST 表示，这些表示更适合分析和执行。

如果您想在不完全重建 Julia 的情况下测试解析器，可以单独运行前端，如下所示：

```
$ cd src
$ flisp/flisp
> (load "jlfrontend.scm")
> (jl-parse-file "<filename>")
```

## [Macro Expansion](@id dev-macro-expansion)

当 [`eval()`](@ref) 遇到宏时，它会在尝试评估表达式之前扩展该 AST 节点。宏扩展涉及从 `4d61726b646f776e2e436f64652822222c20226576616c28292229_40726566`（在 Julia 中）到解析器函数 `jl_macroexpand()`（用 `flisp` 编写），再到 Julia 宏本身（用 - 还有什么 - Julia 编写）通过 `fl_invoke_julia_macro()`，然后再返回。

通常，宏扩展在调用 [`Meta.lower()`](@ref)/`jl_expand()` 时作为第一步被调用，尽管它也可以通过调用 [`macroexpand()`](@ref)/`jl_macroexpand()` 直接调用。

## [Type Inference](@id dev-type-inference)

类型推断在 Julia 中的实现是通过 [`typeinf()` in `compiler/typeinfer.jl`](https://github.com/JuliaLang/julia/blob/master/base/compiler/typeinfer.jl)。类型推断是检查 Julia 函数并确定其每个变量类型的界限，以及函数返回值类型的界限的过程。这使得许多未来的优化成为可能，例如已知不可变值的解包，以及在编译时提升各种运行时操作，如计算字段偏移量和函数指针。类型推断还可能包括其他步骤，例如常量传播和内联。

!!! sidebar "More Definitions"
      * JIT

        即时编译 生成本机代码并在需要时立即加载到内存中的过程。
      * LLVM

        低级虚拟机（编译器）Julia JIT 编译器是一个名为 libLLVM 的程序/库。Julia 中的代码生成既指将 Julia 抽象语法树（AST）转换为 LLVM 指令的过程，也指 LLVM 优化该指令并将其转换为本地汇编指令的过程。
      * C++

        LLVM实现的编程语言，这意味着代码生成也在这种语言中实现。Julia的其余库是用C实现的，部分原因是其较小的特性集使其更易用作为跨语言接口层。
      * 盒子

        此术语用于描述将一个值进行包装的过程，该包装围绕着由垃圾收集器（gc）跟踪的数据，并标记有对象的类型。
      * 开箱

        反向装箱一个值。这种操作使得在编译时完全知道数据类型（通过类型推断）时，可以更高效地操作数据。
      * 通用函数

        一个由多个“方法”组成的Julia函数，这些方法根据参数类型签名进行动态调度。
      * 匿名函数或“方法”

        一个没有名称且没有类型分发能力的 Julia 函数
      * 原始函数

        一个在C中实现但在Julia中作为命名函数“method”暴露的函数（尽管没有通用函数调度能力，类似于匿名函数）
      * 内在函数

        在Julia中以函数形式暴露的低级操作。这些伪函数实现了对原始位的操作，例如加法和符号扩展，这些操作无法以其他方式直接表达。由于它们直接操作位，因此必须编译成一个函数，并用`Core.Intrinsics.box(T, ...)`的调用将类型信息重新分配给该值。


## [JIT Code Generation](@id dev-codegen)

Codegen 是将 Julia AST 转换为本机机器代码的过程。

JIT 环境通过对 [`jl_init_codegen` in `codegen.cpp`](https://github.com/JuliaLang/julia/blob/master/src/codegen.cpp) 的早期调用进行初始化。

根据需要，Julia 方法通过函数 `emit_function(jl_method_instance_t*)` 转换为本地函数。（注意，当使用 MCJIT（在 LLVM v3.4+ 中）时，每个函数必须 JIT 到一个新模块中。）该函数递归调用 `emit_expr()`，直到整个函数被发出。

此文件剩余的大部分内容专门用于对特定代码模式的各种手动优化。例如，`emit_known_call()` 知道如何内联许多原始函数（在 [`builtins.c`](https://github.com/JuliaLang/julia/blob/master/src/builtins.c) 中定义）以适应各种参数类型的组合。

代码生成的其他部分由各种辅助文件处理：

  * [`debuginfo.cpp`](https://github.com/JuliaLang/julia/blob/master/src/debuginfo.cpp)

    处理 JIT 函数的回溯
  * [`ccall.cpp`](https://github.com/JuliaLang/julia/blob/master/src/ccall.cpp)

    处理 ccall 和 llvmcall FFI，以及各种 `abi_*.cpp` 文件
  * [`intrinsics.cpp`](https://github.com/JuliaLang/julia/blob/master/src/intrinsics.cpp)

    处理各种低级内置函数的发射

!!! sidebar "Bootstrapping"
    创建新系统映像的过程称为“引导”。

    这个词的词源来自短语“通过靴带自我提升”，指的是从一组非常有限的可用功能和定义开始，最终创建一个功能齐全的环境的想法。


## [System Image](@id dev-sysimg)

系统映像是一个预编译的 Julia 文件集的归档。与 Julia 一起分发的 `sys.ji` 文件就是这样一个系统映像，它是通过执行文件 [`sysimg.jl`](https://github.com/JuliaLang/julia/blob/master/base/sysimg.jl) 并将生成的环境（包括类型、函数、模块和所有其他定义的值）序列化到文件中而生成的。因此，它包含了 `Main`、`Core` 和 `Base` 模块的冻结版本（以及引导结束时环境中的其他内容）。这个序列化/反序列化器是通过 [`jl_save_system_image`/`jl_restore_system_image` in `staticdata.c`](https://github.com/JuliaLang/julia/blob/master/src/staticdata.c) 实现的。

如果没有 sysimg 文件（`jl_options.image_file == NULL`），这也意味着在命令行中给出了 `--build`，因此最终结果应该是一个新的 sysimg 文件。在 Julia 初始化期间，创建了最小的 `Core` 和 `Main` 模块。然后从当前目录评估一个名为 `boot.jl` 的文件。Julia 然后评估作为命令行参数给出的任何文件，直到达到末尾。最后，它将结果环境保存到一个 "sysimg" 文件中，以便作为未来 Julia 运行的起点。
