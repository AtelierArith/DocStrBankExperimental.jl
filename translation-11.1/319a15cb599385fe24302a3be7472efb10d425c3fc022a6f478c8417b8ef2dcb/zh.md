# Working with LLVM

这不是LLVM文档的替代品，而是关于在Julia中使用LLVM的一些技巧的集合。

## Overview of Julia to LLVM Interface

Julia 默认动态链接 LLVM。使用 `USE_LLVM_SHLIB=0` 进行静态链接。

将Julia AST 降低到 LLVM IR 或直接解释的代码位于 `src/` 目录中。

| File                             | Description                                                        |
|:-------------------------------- |:------------------------------------------------------------------ |
| `aotcompile.cpp`                 | Compiler C-interface entry and object file emission                |
| `builtins.c`                     | Builtin functions                                                  |
| `ccall.cpp`                      | Lowering [`ccall`](@ref)                                           |
| `cgutils.cpp`                    | Lowering utilities, notably for array and tuple accesses           |
| `codegen.cpp`                    | Top-level of code generation, pass list, lowering builtins         |
| `debuginfo.cpp`                  | Tracks debug information for JIT code                              |
| `disasm.cpp`                     | Handles native object file and JIT code diassembly                 |
| `gf.c`                           | Generic functions                                                  |
| `intrinsics.cpp`                 | Lowering intrinsics                                                |
| `jitlayers.cpp`                  | JIT-specific code, ORC compilation layers/utilities                |
| `llvm-alloc-helpers.cpp`         | Julia-specific escape analysis                                     |
| `llvm-alloc-opt.cpp`             | Custom LLVM pass to demote heap allocations to the stack           |
| `llvm-cpufeatures.cpp`           | Custom LLVM pass to lower CPU-based functions (e.g. haveFMA)       |
| `llvm-demote-float16.cpp`        | Custom LLVM pass to lower 16b float ops to 32b float ops           |
| `llvm-final-gc-lowering.cpp`     | Custom LLVM pass to lower GC calls to their final form             |
| `llvm-gc-invariant-verifier.cpp` | Custom LLVM pass to verify Julia GC invariants                     |
| `llvm-julia-licm.cpp`            | Custom LLVM pass to hoist/sink Julia-specific intrinsics           |
| `llvm-late-gc-lowering.cpp`      | Custom LLVM pass to root GC-tracked values                         |
| `llvm-lower-handlers.cpp`        | Custom LLVM pass to lower try-catch blocks                         |
| `llvm-muladd.cpp`                | Custom LLVM pass for fast-match FMA                                |
| `llvm-multiversioning.cpp`       | Custom LLVM pass to generate sysimg code on multiple architectures |
| `llvm-propagate-addrspaces.cpp`  | Custom LLVM pass to canonicalize addrspaces                        |
| `llvm-ptls.cpp`                  | Custom LLVM pass to lower TLS operations                           |
| `llvm-remove-addrspaces.cpp`     | Custom LLVM pass to remove Julia addrspaces                        |
| `llvm-remove-ni.cpp`             | Custom LLVM pass to remove Julia non-integral addrspaces           |
| `llvm-simdloop.cpp`              | Custom LLVM pass for [`@simd`](@ref)                               |
| `pipeline.cpp`                   | New pass manager pipeline, pass pipeline parsing                   |
| `sys.c`                          | I/O and operating system utility functions                         |

一些 `.cpp` 文件组成一个组，编译成一个单一的对象。

内置函数和内在函数之间的区别在于，内置函数是可以像其他任何Julia函数一样使用的一等函数。内在函数只能对未包装的数据进行操作，因此其参数必须是静态类型。

### [Alias Analysis](@id LLVM-Alias-Analysis)

Julia currently uses LLVM's [Type Based Alias Analysis](https://llvm.org/docs/LangRef.html#tbaa-metadata). To find the comments that document the inclusion relationships, look for `static MDNode*` in `src/codegen.cpp`.

`-O` 选项启用 LLVM 的 [Basic Alias Analysis](https://llvm.org/docs/AliasAnalysis.html#the-basic-aa-pass)。

## Building Julia with a different version of LLVM

LLVM的默认版本在`deps/llvm.version`中指定。您可以通过在顶层目录中创建一个名为`Make.user`的文件并添加一行，例如：

```
LLVM_VER = 13.0.0
```

除了 LLVM 发布版本号，您还可以使用 `DEPS_GIT = llvm` 结合 `USE_BINARYBUILDER_LLVM = 0` 来构建最新开发版本的 LLVM。

您还可以通过在 `Make.user` 文件中设置 `LLVM_DEBUG = 1` 或 `LLVM_DEBUG = Release` 来指定构建 LLVM 的调试版本。前者将是一个完全未优化的 LLVM 构建，而后者将生成一个优化的 LLVM 构建。根据您的需求，后者就足够了，并且速度快得多。如果您使用 `LLVM_DEBUG = Release`，您还需要设置 `LLVM_ASSERTIONS = 1` 以启用不同传递的诊断。只有 `LLVM_DEBUG = 1` 默认意味着该选项。

## Passing options to LLVM

您可以通过环境变量 [`JULIA_LLVM_ARGS`](@ref JULIA_LLVM_ARGS) 向 LLVM 传递选项。以下是使用 `bash` 语法的示例设置：

  * `export JULIA_LLVM_ARGS=-print-after-all` 在每个传递后转储 IR。
  * `export JULIA_LLVM_ARGS=-debug-only=loop-vectorize` 会转储 LLVM `DEBUG(...)` 诊断信息以供循环向量化使用。如果您收到关于“未知命令行参数”的警告，请使用 `LLVM_ASSERTIONS = 1` 重新构建 LLVM。
  * `export JULIA_LLVM_ARGS=-help` 显示可用选项的列表。 `export JULIA_LLVM_ARGS=-help-hidden` 显示更多选项。
  * `export JULIA_LLVM_ARGS="-fatal-warnings -print-options"` 是如何使用多个选项的示例。

### Useful `JULIA_LLVM_ARGS` parameters

  * `-print-after=PASS`：在任何执行 `PASS` 后打印 IR，便于检查通过的更改。
  * `-print-before=PASS`: 在执行任何 `PASS` 之前打印 IR，便于检查传递的输入。
  * `-print-changed`: 当一个传递改变了 IR 时打印 IR，便于缩小导致问题的传递范围。
  * `-print-(before|after)=MARKER-PASS`：Julia 管道附带了一些标记传递，可以用来识别问题或优化发生的位置。标记传递被定义为在管道中出现一次且对 IR 不进行任何转换的传递，仅用于定位 print-before/print-after。目前，管道中存在以下标记传递：

      * 在优化之前
      * 在早期简化之前
      * 在早期简化之后
      * 在早期优化之前
      * 在早期优化之后
      * 在循环前优化
      * 在LICM之前
      * AfterLICM
      * 在循环前简化
      * AfterLoopSimplification
      * AfterLoopOptimization
      * 在标量优化之前
      * AfterScalarOptimization
      * 在向量化之前
      * 在向量化之后
      * BeforeIntrinsicLowering
      * 在内在降低之后
      * 在清理之前
      * AfterCleanup
      * 在优化后
  * `-time-passes`: 打印每个通行所花费的时间，便于识别哪些通行耗时较长。
  * `-print-module-scope`：与 `-print-(before|after)` 一起使用，获取整个模块，而不是传递给该传递的 IR 单元。
  * `-debug`: 在整个LLVM中打印大量调试信息
  * `-debug-only=NAME`，打印出来自定义为 `NAME` 的文件中的调试语句，便于获取有关问题的额外上下文。

## Debugging LLVM transformations in isolation

有时，单独调试LLVM的转换对于整个Julia系统是有用的，例如，因为在`julia`内部重现问题会花费太长时间，或者因为人们想利用LLVM的工具（例如bugpoint）。

要开始，您可以通过以下方式安装开发工具以使用LLVM：

```
make -C deps install-llvm-tools
```

要获取整个系统映像的未优化 IR，请在系统映像构建过程中传递 `--output-unopt-bc unopt.bc` 选项，这将把未优化的 IR 输出到 `unopt.bc` 文件中。然后可以像往常一样将此文件传递给 LLVM 工具。`libjulia` 可以作为 LLVM 传递插件，并可以加载到 LLVM 工具中，以便在此环境中提供特定于 Julia 的传递。此外，它还暴露了 `-julia` 元传递，该传递在 IR 上运行整个 Julia 传递管道。作为示例，要使用旧的传递管理器生成系统映像，可以执行：

```

llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

要生成带有新密码管理器的系统映像，可以执行：

```
opt -load-pass-plugin=libjulia-codegen.so --passes='julia' -o opt.bc unopt.bc
llc -o sys.o opt.bc
cc -shared -o sys.so sys.o
```

此系统映像可以像往常一样通过 `julia` 加载。

也可以仅为一个 Julia 函数转储 LLVM IR 模块，使用：

```julia
fun, T = +, Tuple{Int,Int} # Substitute your function of interest here
optimize = false
open("plus.ll", "w") do file
    println(file, InteractiveUtils._dump_function(fun, T, false, false, false, true, :att, optimize, :default, false))
end
```

这些文件可以与上面显示的未优化 sysimg IR 以相同的方式处理。

## Running the LLVM test suite

要在本地运行llvm测试，您需要首先安装工具，构建julia，然后您可以运行测试：

```
make -C deps install-llvm-tools
make -j julia-src-release
make -C test/llvmpasses
```

如果您想直接通过每个测试文件顶部的命令运行单个测试文件，第一步将在 `./usr/tools/opt` 中安装工具。然后，您需要手动将 `%s` 替换为测试文件的名称。

## Improving LLVM optimizations for Julia

改善 LLVM 代码生成通常涉及要么改变 Julia 的降级，使其更适合 LLVM 的传递，要么改进一个传递。

如果您计划改进一个传递，请务必阅读 [LLVM developer policy](https://llvm.org/docs/DeveloperPolicy.html)。最佳策略是创建一个代码示例，以便您可以使用 LLVM 的 `opt` 工具单独研究它和感兴趣的传递。

1. 请提供您想要翻译的Markdown内容或文本。
2. 使用 `JULIA_LLVM_ARGS=-print-after-all` 来转储 IR。
3. 在感兴趣的传球运行之前，挑选出IR。
4. 剥离调试元数据并手动修复TBAA元数据。

最后一步劳动强度大。对于更好的方法的建议将不胜感激。

## The jlcall calling convention

Julia 有一个通用的调用约定用于未优化的代码，具体如下：

```c
jl_value_t *any_unoptimized_call(jl_value_t *, jl_value_t **, int);
```

其中第一个参数是被封装的函数对象，第二个参数是一个栈上的参数数组，第三个参数是参数的数量。现在，我们可以进行直接的降级并为参数数组发出一个alloca。然而，这将背离调用点使用的SSA特性，使得优化（包括GC根位置的放置）变得显著困难。相反，我们将其发出如下：

```llvm
call %jl_value_t *@julia.call(jl_value_t *(*)(...) @any_unoptimized_call, %jl_value_t *%arg1, %jl_value_t *%arg2)
```

这使我们能够在优化器中保留使用的SSA特性。GC根位置稍后将把此调用降低到原始C ABI。

## GC root placement

GC 根位置的放置是在 LLVM 的传递管道后期完成的。如此晚进行 GC 根位置的放置使得 LLVM 能够在需要 GC 根的代码周围进行更激进的优化，同时也允许我们减少所需的 GC 根和 GC 根存储操作的数量（由于 LLVM 不理解我们的 GC，因此它不会知道可以对存储到 GC 帧的值做什么，因此它会保守地做很少的操作）。作为一个例子，考虑一个错误路径。

```julia
if some_condition()
    #= Use some variables maybe =#
    error("An error occurred")
end
```

在常量折叠过程中，LLVM 可能会发现条件始终为假，并可以删除基本块。然而，如果 GC 根降低过早进行，则在被删除的块中使用的 GC 根槽以及仅因在错误路径中使用而保持存活的任何值将被 LLVM 保持存活。通过延迟进行 GC 根降低，我们给予 LLVM 进行任何常规优化（常量折叠、死代码消除等）的许可，而不必过于担心哪些值可能会或可能不会被 GC 跟踪。

然而，为了能够进行延迟的 GC 根位置放置，我们需要能够识别 a) 哪些指针是 GC 跟踪的，以及 b) 所有使用这些指针的地方。因此，GC 放置阶段的目标是简单的：

最小化所需的 GC 根/存储数量，前提是每个安全点处，任何活跃的 GC 跟踪指针（即在此点之后存在路径包含该指针的使用）都在某个 GC 槽中。

### Representation

主要的困难在于选择一种 IR 表示，使我们能够识别 GC 跟踪的指针及其使用，即使在程序经过优化器处理之后。我们的设计利用了三个 LLVM 特性来实现这一点：

  * 自定义地址空间
  * 操作数捆绑包
  * 非整数指针

自定义地址空间允许我们为每个点标记一个需要在优化过程中保留的整数。编译器可能不会在原始程序中不存在的地址空间之间插入转换，并且在加载/存储等操作中绝不能更改指针的地址空间。这使我们能够以抗优化的方式注释哪些指针是由垃圾回收（GC）跟踪的。请注意，元数据无法实现相同的目的。元数据应该始终是可丢弃的，而不改变程序的语义。然而，未能识别出一个由GC跟踪的指针会显著改变结果程序的行为——它可能会崩溃或返回错误的结果。我们目前使用三种不同的地址空间（它们的编号在 `src/codegen_shared.cpp` 中定义）：

  * GC 跟踪指针（当前为 10）：这些是指向可能被放入 GC 框架的盒装值的指针。它在 C 端大致相当于 `jl_value_t*` 指针。注意：在这个地址空间中，任何可能不被存储到 GC 槽的指针都是非法的。
  * 派生指针（目前有 11 个）：这些是从某个 GC 跟踪的指针派生出来的指针。这些指针的使用会导致原始指针的使用。然而，它们不必自己被 GC 知道。GC 根放置阶段必须始终找到从中派生出该指针的 GC 跟踪指针，并将其用作根指针。
  * 被调用者根指针（当前为 12）：这是一个实用的地址空间，用于表达被调用者根值的概念。该地址空间的所有值必须可存储到 GC 根（尽管将来可能会放宽此条件），但与其他指针不同，如果传递给调用，则不需要根（如果它们在定义和调用之间的另一个安全点之间仍然存活，则仍然需要根）。
  * 从跟踪对象加载的指针（当前为 13）：这被数组使用，数组本身包含指向托管数据的指针。该数据区域由数组拥有，但本身不是 GC 跟踪的对象。编译器保证，只要这个指针是活跃的，从中加载该指针的对象将保持活跃。

### Invariants

GC根放置阶段利用了几个不变式，这些不变式需要由前端遵守，并由优化器保持。

首先，仅允许以下地址空间转换：

  * 0->{跟踪的,派生的,被调用根}: 允许将未跟踪的指针衰减为其他任何指针。然而，请注意，优化器有广泛的权限来不根植这样的值。如果一个值在程序的任何部分位于地址空间0，并且它是（或源自）一个需要GC根的值，那么这样做永远是不安全的。
  * 跟踪->派生：这是内部值的标准衰减路径。放置通道将查找这些以识别任何使用的基指针。
  * Tracked->CalleeRooted: Addrspace CalleeRooted 仅仅作为一个提示，表明不需要 GC 根。然而，请注意，Derived->CalleeRooted 的衰减是被禁止的，因为指针通常应该可以存储到 GC 槽中，即使在这个地址空间中。

现在让我们考虑什么构成使用：

  * 加载其加载值位于某个地址空间中的负载
  * 将一个地址空间中的值存储到一个位置
  * 将指针存储到某个地址空间中
  * 在其中一个地址空间中的值作为操作数的调用
  * 在 jlcall ABI 中，参数数组包含一个值的调用
  * 请提供您希望翻译的Markdown内容或文本。

我们明确允许在地址空间 Tracked/Derived 中进行加载/存储和简单调用。jlcall 参数数组的元素必须始终位于地址空间 Tracked（这是 ABI 要求它们是有效的 `jl_value_t*` 指针）。返回指令也是如此（尽管请注意，结构返回参数可以具有任何地址空间）。CalleeRooted 指针的唯一允许使用是将其传递给调用（该调用必须具有适当类型的操作数）。

此外，我们不允许在地址空间 Tracked 中使用 `getelementptr`。这是因为除非该操作是无操作（noop），否则生成的指针将无法有效地存储到 GC 槽中，因此可能不在此地址空间。如果需要这样的指针，应首先将其衰减为地址空间 Derived。

最后，我们不允许在这些地址空间中使用 `inttoptr`/`ptrtoint` 指令。拥有这些指令意味着某些 `i64` 值实际上是被 GC 跟踪的。这是有问题的，因为它破坏了我们能够识别与 GC 相关的指针这一声明的要求。这个不变性是通过使用 LLVM 的“非整数指针”特性来实现的，该特性在 LLVM 5.0 中引入。它禁止优化器进行可能引入这些操作的优化。请注意，我们仍然可以通过在地址空间 0 中使用 `inttoptr` 在 JIT 时插入静态常量，然后再衰减到适当的地址空间。

### Supporting [`ccall`](@ref)

一个到目前为止讨论中缺失的重要方面是对 [`ccall`](@ref) 的处理。 `4d61726b646f776e2e436f64652822222c20226363616c6c2229_40726566` 具有一个特殊的特征，即使用的位置和范围不一致。作为一个例子，考虑：

```julia
A = randn(1024)
ccall(:foo, Cvoid, (Ptr{Float64},), A)
```

在降级过程中，编译器会插入一个从数组到指针的转换，这会丢失对数组值的引用。然而，我们当然需要确保在执行 [`ccall`](@ref) 时数组仍然存在。为了理解这是如何实现的，让我们看看上述代码的一个假设性近似降级：

```julia
return $(Expr(:foreigncall, :(:foo), Cvoid, svec(Ptr{Float64}), 0, :(:ccall), Expr(:foreigncall, :(:jl_array_ptr), Ptr{Float64}, svec(Any), 0, :(:ccall), :(A)), :(A)))
```

最后的 `:(A)` 是在降低过程中插入的额外参数列表，它通知代码生成器在此 [`ccall`](@ref) 的持续时间内需要保持活跃的 Julia 级别值。然后，我们将这些信息表示为 IR 级别的“操作数捆绑”。操作数捆绑本质上是附加到调用站点的虚假使用。在 IR 级别，这看起来是这样的：

```llvm
call void inttoptr (i64 ... to void (double*)*)(double* %5) [ "jl_roots"(%jl_value_t addrspace(10)* %A) ]
```

GC 根放置通道将把 `jl_roots` 操作数包视为常规操作数。然而，作为最后一步，在插入 GC 根之后，它将删除操作数包，以避免混淆指令选择。

### Supporting [`pointer_from_objref`](@ref)

[`pointer_from_objref`](@ref) 是特别的，因为它要求用户显式控制 GC 根。根据我们上述的不变性，这个函数是非法的，因为它将地址空间从 10 转换为 0。然而，在某些情况下，它可能是有用的，因此我们提供了一个特殊的内在函数：

```llvm
declared %jl_value_t *julia.pointer_from_objref(%jl_value_t addrspace(10)*)
```

在垃圾回收根降低后，相应的地址空间转换被降低。然而，请注意，通过使用这个内在函数，调用者承担确保相关值被根植的所有责任。此外，这个内在函数不被视为使用，因此垃圾回收根放置阶段不会为该函数提供垃圾回收根。因此，外部根植必须在系统仍然跟踪该值时进行安排。也就是说，尝试使用此操作的结果来建立全局根是不合法的——优化器可能已经丢弃了该值。

### Keeping values alive in the absence of uses

在某些情况下，有必要保持一个对象的存活，即使该对象没有被编译器可见地使用。这可能适用于直接操作对象内存表示的低级代码或需要与 C 代码接口的代码。为了允许这一点，我们在 LLVM 级别提供以下内置函数：

```
token @llvm.julia.gc_preserve_begin(...)
void @llvm.julia.gc_preserve_end(token)
```

（名称中的 `llvm.` 是必需的，以便能够使用 `token` 类型）。这些内置函数的语义如下：在任何由 `gc_preserve_begin` 调用主导的安全点，但未被相应的 `gc_preserve_end` 调用主导（即，参数是由 `gc_preserve_begin` 调用返回的 token 的调用），传递给该 `gc_preserve_begin` 的值将保持活跃。请注意，`gc_preserve_begin` 仍然算作对这些值的常规使用，因此标准的生命周期语义将确保在进入保护区域之前，这些值将保持活跃。
