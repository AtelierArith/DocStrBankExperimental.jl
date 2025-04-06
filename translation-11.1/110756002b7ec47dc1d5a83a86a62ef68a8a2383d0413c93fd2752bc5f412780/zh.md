# Custom LLVM Passes

Julia 有许多自定义的 LLVM 传递。大体上，它们可以分为两类：一类是为了维护 Julia 语义而必须运行的传递，另一类是利用 Julia 语义来优化 LLVM IR 的传递。

## Semantic Passes

这些传递用于将LLVM IR转换为可以在CPU上运行的代码。它们的主要目的是使代码生成能够发出更简单的IR，从而使其他LLVM传递能够优化常见模式。

### CPUFeatures

  * 文件名：`llvm-cpufeatures.cpp`
  * 类名：`CPUFeaturesPass`
  * 选项名称: `module(CPUFeatures)`

此通行证将 `julia.cpu.have_fma.(f32|f64)` 内在函数降低为真或假，具体取决于目标架构和函数中存在的目标特性。此内在函数通常用于确定使用依赖于快速 [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) 操作的算法是否优于使用不依赖于此类指令的标准算法。

### DemoteFloat16

  * 文件名: `llvm-demote-float16.cpp`
  * 类名: `DemoteFloat16Pass`
  * 选项名称 `function(DemoteFloat16)`

此传递将 [float16](https://en.wikipedia.org/wiki/Half-precision_floating-point_format) 操作替换为 float32 操作，适用于不原生支持 float16 操作的架构。通过在任何 float16 操作周围插入 `fpext` 和 `fptrunc` 指令来实现。在支持原生 float16 操作的架构上，此传递是一个无操作。

### LateGCLowering

  * 文件名：`llvm-late-gc-lowering.cpp`
  * 类名：`LateLowerGCPass`
  * 选项名称: `function(LateLowerGCFrame)`

此通行证执行了大部分所需的 GC 根工作，以跟踪 GC 安全点之间的指针。它还将多个内在函数降低到其相应的指令翻译，并被允许违反先前建立的非整数不变性（`pointer_from_objref` 在这里被降低为 `ptrtoint` 指令）。由于其数据流算法旨在最小化任何安全点处活动对象的数量，此通行证通常占用所有自定义 Julia 通行证中最多的时间。

### FinalGCLowering

  * 文件名：`llvm-final-gc-lowering.cpp`
  * 类名：`FinalLowerGCPass`
  * Opt Name: `module(FinalLowerGC)`

此通行证将一些最后的内在函数降低到其最终形式，目标是 `libjulia` 库中的函数。将其与 `LateGCLowering` 分开，使其他后端（GPU 编译）能够为这些内在函数提供自定义的降低，从而使 Julia 管道也可以在这些后端上使用。

### LowerHandlers

  * 文件名：`llvm-lower-handlers.cpp`
  * 类名：`LowerExcHandlersPass`
  * 选项名称: `function(LowerExcHandlers)`

此传递将异常处理内在函数降低为在处理异常时实际调用的运行时函数的调用。

### RemoveNI

  * 文件名：`llvm-remove-ni.cpp`
  * 类名：`RemoveNIPass`
  * 选项名称: `module(RemoveNI)`

此通行证从模块的数据布局字符串中移除非整数地址空间。这使得后端能够将Julia的自定义地址空间直接降低为机器代码，而无需对每个指针操作进行昂贵的重写以指向地址空间0。

### SIMDLoop

  * 文件名：`llvm-simdloop.cpp`
  * 类名：`LowerSIMDLoopPass`
  * Opt 名称: `loop(LowerSIMDLoop)`

此传递作为 `@simd` 注释的主要驱动程序。代码生成在循环的后向分支插入 `!llvm.loopid` 标记，该传递使用此标记来识别最初标记为 `@simd` 的循环。然后，此传递查找形成归约的浮点运算链，并添加 `contract` 和 `reassoc` 快速数学标志以允许重新关联（从而实现向量化）。此传递不保留任何循环信息或推理正确性，因此可能以令人惊讶的方式违反 Julia 语义。如果循环也被注释为 `ivdep`，则该传递将循环标记为没有循环携带依赖关系（如果用户注释不正确或应用于错误的循环，则结果行为是未定义的）。

### LowerPTLS

  * 文件名：`llvm-ptls.cpp`
  * 类名：`LowerPTLSPass`
  * Opt 名称: `module(LowerPTLSPass)`

此传递将线程局部的Julia内置函数降低为汇编指令。Julia依赖线程局部存储进行垃圾回收和多线程任务调度。在为系统映像和包映像编译代码时，此传递将对内置函数的调用替换为在加载时初始化的全局变量的加载。

如果代码生成产生了一个带有 `swiftself` 参数和调用约定的函数，则此传递假定 `swiftself` 参数是 pgcstack，并将用该参数替换内置函数。这样做可以在具有较慢线程本地存储访问的架构上提供加速。

### RemoveAddrspaces

  * 文件名：`llvm-remove-addrspaces.cpp`
  * 类名：`RemoveAddrspacesPass`
  * Opt 名称: `module(RemoveAddrspaces)`

此通行将一个地址空间中的指针重命名为另一个地址空间。这用于从LLVM IR中移除特定于Julia的地址空间。

### RemoveJuliaAddrspaces

  * 文件名: `llvm-remove-addrspaces.cpp`
  * 类名：`RemoveJuliaAddrspacesPass`
  * Opt 名称: `module(RemoveJuliaAddrspaces)`

此通行证从LLVM IR中移除Julia特定的地址空间。它主要用于以更简洁的格式显示LLVM IR。内部实现基于RemoveAddrspaces通行证。

### Multiversioning

  * 文件名：`llvm-multiversioning.cpp`
  * 类名：`MultiVersioningPass`
  * Opt 名称: `module(JuliaMultiVersioning)`

此传递对模块进行修改，以创建针对不同架构优化的函数（有关更多详细信息，请参见 sysimg.md 和 pkgimg.md）。在实现方面，它克隆函数并应用不同的目标特定属性，以允许优化器使用该平台的高级功能，例如向量化和指令调度。它还创建了一些基础设施，以使 Julia 图像加载器能够根据加载器运行的架构选择要调用的函数的适当版本。目标特定属性由 `julia.mv.specs` 模块标志控制，该标志在编译期间源自环境变量 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET)。该传递还必须通过提供值为 1 的 `julia.mv.enable` 模块标志来启用。

!!! warning
    使用 `llvmcall` 进行多版本化是危险的。`llvmcall` 允许访问通常不通过 Julia API 暴露的特性，因此通常在所有架构上不可用。如果启用了多版本化，并且请求为不支持 `llvmcall` 表达式所需特性的目标架构生成代码，LLVM 可能会出错，通常会中止并显示消息 `LLVM ERROR: Do not know how to split the result of this operator!`。


### GCInvariantVerifier

  * 文件名: `llvm-gc-invariant-verifier.cpp`
  * 类名：`GCInvariantVerifierPass`
  * 选项名称: `module(GCInvariantVerifier)`

此通行证用于验证Julia关于LLVM IR的不变性。这包括诸如Julia的[non-integral address spaces](https://llvm.org/docs/LangRef.html#non-integral-pointer-type) [^nislides]中`ptrtoint`的不存在，以及仅存在受祝福的`addrspacecast`指令（Tracked -> Derived，0 -> Tracked等）。它对IR不进行任何变换。

[^nislides]: https://llvm.org/devmtg/2015-02/slides/chisnall-pointers-not-int.pdf

## Optimization Passes

这些传递用于对LLVM IR执行LLVM本身不会执行的转换，例如快速数学标志传播、逃逸分析以及对Julia特定内部函数的优化。它们利用对Julia语义的知识来执行这些优化。

### CombineMulAdd

  * 文件名: `llvm-muladd.cpp`
  * 类名：`CombineMulAddPass`
  * 选项名称: `function(CombineMulAdd)`

此通行证旨在优化常规 `fmul` 与快速 `fadd` 的特定组合为一个合约 `fmul` 与快速 `fadd`。随后，后端将其优化为 [fused multiply-add](https://en.wikipedia.org/wiki/Multiply%E2%80%93accumulate_operation#Fused_multiply%E2%80%93add) 指令，这可以以更快的速度提供显著更快的操作，代价是更多的 [unpredictable semantics](https://simonbyrne.github.io/notes/fastmath/)。

!!! note
    此优化仅在 `fmul` 只有一个使用时发生，即快速的 `fadd`。


### AllocOpt

  * 文件名：`llvm-alloc-opt.cpp`
  * 类名：`AllocOptPass`
  * 选项名称: `function(AllocOpt)`

Julia 并没有将程序栈作为分配可变对象的概念。然而，在栈上分配对象可以减少 GC 压力，并且对 GPU 编译至关重要。因此，`AllocOpt` 执行对象的堆到栈转换，它可以证明这些对象不会 [escape](https://en.wikipedia.org/wiki/Escape_analysis) 当前函数。它还对分配执行了一些其他优化，例如移除从未使用的分配，优化对新分配对象的 typeof 调用，以及移除立即被覆盖的分配的存储。逃逸分析的实现位于 `llvm-alloc-helpers.cpp`。目前，这个传递不使用来自 `EscapeAnalysis.jl` 的信息，尽管未来可能会有所改变。

### PropagateJuliaAddrspaces

  * 文件名：`llvm-propagate-addrspaces.cpp`
  * 类名：`PropagateJuliaAddrspacesPass`
  * Opt 名称: `function(PropagateJuliaAddrspaces)`

此通行证用于通过指针上的操作传播特定于Julia的地址空间。LLVM不允许通过优化引入或删除addrspacecast指令，因此此通行证的作用是通过用Julia地址空间中的等效操作替换操作来消除冗余的addrspace转换。有关Julia地址空间的更多信息，请参见（TODO链接到llvm.md）。

### JuliaLICM

  * 文件名: `llvm-julia-licm.cpp`
  * 类名：`JuliaLICMPass`
  * Opt 名称: `loop(JuliaLICM)`

此通行证用于将特定于Julia的内在函数提升出循环。具体来说，它执行以下转换：

1. 将 `gc_preserve_begin` 提升并将 `gc_preserve_end` 降低到循环外部，当被保护的对象是循环不变时。

    1. 由于在循环中保留的对象可能会在循环的持续时间内被保留，因此这种转换可以减少 IR 中 `gc_preserve_begin`/`gc_preserve_end` 对的数量。这使得 `LateLowerGCPass` 更容易识别特定对象被保留的位置。
2. 提升具有不变对象的写屏障

    1. 在这里，我们假设一个对象只能属于两个代。基于此，对于任何一对相同的对象，写屏障只需要执行一次。因此，当被写入的对象是循环不变时，我们可以将写屏障提升出循环。
3. 将不逃逸循环的分配提升到循环外部

    1. 我们在这里使用非常保守的逃逸定义，与 `AllocOptPass` 中使用的定义相同。即使一个分配完全逃逸了函数，这种转换也可以减少 IR 中的分配数量。

!!! note
    此通行证是为了保护LLVM的[MemorySSA](https://llvm.org/docs/MemorySSA.html)（[Short Video](https://www.youtube.com/watch?v=bdxWmryoHak)，[Longer Video](https://www.youtube.com/watch?v=1e5y6WDbXCQ)）和[ScalarEvolution](https://baziotis.cs.illinois.edu/compilers/introduction-to-scalar-evolution.html)（[Newer Slides](https://llvm.org/devmtg/2018-04/slides/Absar-ScalarEvolution.pdf) [Older Slides](https://llvm.org/devmtg/2009-10/ScalarEvolutionAndLoopOptimization.pdf)）分析。

