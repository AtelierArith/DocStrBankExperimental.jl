# JIT Design and Implementation

本文档解释了Julia的JIT的设计和实现，在代码生成完成并生成未优化的LLVM IR之后。JIT负责优化和编译此IR为机器代码，并将其链接到当前进程中，使代码可供执行。

## Introduction

JIT 负责管理编译资源，查找先前编译的代码，并编译新代码。它主要基于 LLVM 的 [On-Request-Compilation](https://llvm.org/docs/ORCv2.html) (ORCv2) 技术构建，支持许多有用的功能，如并发编译、延迟编译以及在单独进程中编译代码的能力。尽管 LLVM 提供了基本的 JIT 编译器 LLJIT，Julia 直接使用许多 ORCv2 API 来创建其自定义 JIT 编译器。

## Overview

![编译器流程图](./img/compiler_diagram.png)

Codegen 生成一个 LLVM 模块，其中包含来自原始 Julia SSA IR 的一个或多个 Julia 函数的 IR，该 IR 由类型推断生成（在上面的编译器图中标记为 translate）。它还生成了代码实例与 LLVM 函数名称的映射。然而，尽管 Julia 基于的编译器对 Julia IR 应用了一些优化，但 Codegen 生成的 LLVM IR 仍然包含许多优化的机会。因此，JIT 的第一步是对 LLVM 模块运行一个与目标无关的优化管道[^tdp]。然后，JIT 运行一个与目标相关的优化管道，其中包括特定于目标的优化和代码生成，并输出一个目标文件。最后，JIT 将生成的目标文件链接到当前进程中，并使代码可供执行。所有这些都由 `src/jitlayers.cpp` 中的代码控制。

[^tdp]: This is not a totally-target independent pipeline, as transformations such as vectorization rely upon target information such as vector register width and cost modeling. Additionally, codegen itself makes a few target-dependent assumptions, and the optimization pipeline will take advantage of that knowledge.

目前，由于我们的一款链接器（RuntimeDyld）施加的限制，优化-编译-链接管道一次只允许一个线程进入。然而，JIT 设计上支持并发优化和编译，预计在未来当 RuntimeDyld 在所有平台上完全被取代时，链接器的限制将会解除。

## Optimization Pipeline

优化管道基于LLVM的新传递管理器，但该管道是根据Julia的需求进行定制的。管道在`src/pipeline.cpp`中定义，通常经过多个阶段，如下所述。

1. 早期简化

    1. 这些传递主要用于简化中间表示（IR）并规范化模式，以便后续的传递能够更容易地识别这些模式。此外，各种内在调用，如分支预测提示和注释，被降低为其他元数据或其他IR特性。 [`SimplifyCFG`](https://llvm.org/docs/Passes.html#simplifycfg-simplify-the-cfg)（简化控制流图），[`DCE`](https://llvm.org/docs/Passes.html#dce-dead-code-elimination)（死代码消除），以及[`SROA`](https://llvm.org/docs/Passes.html#sroa-scalar-replacement-of-aggregates)（聚合体的标量替换）是这里的一些关键角色。
2. 早期优化

    1. 这些传递通常很便宜，主要集中在减少 IR 中的指令数量和将知识传播到其他指令。例如，[`EarlyCSE`](https://en.wikipedia.org/wiki/Common_subexpression_elimination) 用于执行公共子表达式消除，而 [`InstCombine`](https://llvm.org/docs/Passes.html#instcombine-combine-redundant-instructions) 和 [`InstSimplify`](https://llvm.org/doxygen/classllvm_1_1InstSimplifyPass.html#details) 执行了一些小的窥视优化，以降低操作的成本。
3. 循环优化

    1. 这些传递对循环进行规范化和简化。循环通常是热点代码，这使得循环优化对性能极为重要。这里的关键参与者包括 [`LoopRotate`](https://llvm.org/docs/Passes.html#loop-rotate-rotate-loops)、[`LICM`](https://llvm.org/docs/Passes.html#licm-loop-invariant-code-motion) 和 [`LoopFullUnroll`](https://llvm.org/docs/Passes.html#loop-unroll-unroll-loops)。某些边界检查消除也在这里发生，作为 [`IRCE`](https://llvm.org/doxygen/InductiveRangeCheckElimination_8cpp_source.html) 传递的结果，该传递可以证明某些边界永远不会被超越。
4. 标量优化

    1. 标量优化管道包含一些更昂贵但更强大的过程，例如 [`GVN`](https://llvm.org/docs/Passes.html#gvn-global-value-numbering)（全局值编号）、[`SCCP`](https://llvm.org/docs/Passes.html#sccp-sparse-conditional-constant-propagation)（稀疏条件常量传播）以及另一轮边界检查消除。这些过程虽然昂贵，但通常可以移除大量代码，使向量化更加成功和有效。几个其他简化和优化过程穿插在更昂贵的过程中，以减少它们需要做的工作量。
5. 向量化

    1. [Automatic vectorization](https://en.wikipedia.org/wiki/Automatic_vectorization) 是一种极其强大的转换，用于 CPU 密集型代码。简而言之，向量化允许执行 [single instruction on multiple data](https://en.wikipedia.org/wiki/Single_instruction,_multiple_data) (SIMD)，例如同时执行 8 次加法操作。然而，证明代码既能够向量化又对向量化有利是困难的，这在很大程度上依赖于先前的优化过程，以将 IR 调整到一个值得进行向量化的状态。
6. 内在降低

    1. Julia 插入了一些自定义内置函数，原因包括对象分配、垃圾回收和异常处理。这些内置函数最初是为了使优化机会更加明显而放置的，但现在它们被降低为 LLVM IR，以便将 IR 转换为机器代码。
7. 清理

    1. 这些通道是最后机会的优化，执行小规模的优化，例如融合乘加传播和除法余数简化。此外，不支持半精度浮点数的目标将在此处将其半精度指令降低为单精度指令，并添加通道以提供清理器支持。

## Target-Dependent Optimization and Code Generation

LLVM 提供了目标依赖的优化和机器代码生成，这些功能位于特定平台的 TargetMachine 中。这些过程包括指令选择、指令调度、寄存器分配和机器代码生成。LLVM 文档提供了该过程的良好概述，而 LLVM 源代码是查找管道和过程详细信息的最佳地方。

## Linking

目前，Julia 正在两个链接器之间过渡：较旧的 RuntimeDyld 链接器和较新的 [JITLink](https://llvm.org/docs/JITLink.html) 链接器。JITLink 包含许多 RuntimeDyld 所不具备的功能，例如并发和可重入链接，但目前缺乏良好的分析集成支持，并且尚未支持 RuntimeDyld 支持的所有平台。随着时间的推移，JITLink 预计将完全取代 RuntimeDyld。有关 JITLink 的更多详细信息，请参阅 LLVM 文档。

## Execution

一旦代码被链接到当前进程，它就可以执行。这个事实通过适当地更新 `invoke`、`specsigflags` 和 `specptr` 字段来通知生成的 codeinst。Codeinst 支持升级 `invoke`、`specsigflags` 和 `specptr` 字段，只要在任何给定时间存在的这些字段的每种组合都是有效的。这允许 JIT 更新这些字段而不使现有的 codeinst 无效，从而支持未来可能的并发 JIT。具体来说，以下状态可能是有效的：

1. `invoke` 是 NULL，`specsigflags` 是 0b00，`specptr` 是 NULL

    1. 这是代码实例的初始状态，表示该代码实例尚未被编译。
2. `invoke` 不是 null，`specsigflags` 是 0b00，`specptr` 是 NULL

    1. 这表明代码实例没有经过任何特化编译，代码实例应该直接调用。请注意，在这种情况下，`invoke` 不会读取 `specsigflags` 或 `specptr` 字段，因此可以在不使 `invoke` 指针失效的情况下修改它们。
3. `invoke` 是非空的，`specsigflags` 是 0b10，`specptr` 是非空的

    1. 这表明代码实例已被编译，但代码生成认为不需要专门的函数签名。
4. `invoke` 是非空的，`specsigflags` 是 0b11，`specptr` 是非空的

    1. 这表明代码实例已被编译，并且代码生成认为有必要使用专门的函数签名。`specptr` 字段包含指向专门函数签名的指针。`invoke` 指针被允许读取 `specsigflags` 和 `specptr` 字段。

此外，在更新过程中会出现多种不同的过渡状态。为了应对这些潜在情况，在处理这些 codeinst 字段时应使用以下写入和读取模式。

1. 在编写 `invoke`、`specsigflags` 和 `specptr` 时：

    1. 执行一个原子比较-交换操作，假设旧值为 NULL。这个比较-交换操作应该至少具有获取-释放顺序，以提供写入中其余内存操作的顺序保证。
    2. 如果 `specptr` 非空，则停止写入操作，并等待 `specsigflags` 的位 0b10 被写入。
    3. 将 `specsigflags` 的新低位写入其最终值。这可能是一个放宽的写入。
    4. 将新的 `invoke` 指针写入其最终值。这必须至少具有释放内存顺序，以便与对 `invoke` 的读取进行同步。
    5. 将 `specsigflags` 的第二位设置为 1。这必须至少是释放内存顺序，以便与对 `specsigflags` 的读取进行同步。此步骤完成写操作，并向所有其他线程宣布所有字段已被设置。
2. 在读取 `invoke`、`specsigflags` 和 `specptr` 时：

    1. 读取 `invoke` 字段，至少使用获取内存顺序。此加载将被称为 `initial_invoke`。
    2. 如果 `initial_invoke` 为 NULL，则 codeinst 尚不可执行。`invoke` 为 NULL，`specsigflags` 可以视为 0b00，`specptr` 可以视为 NULL。
    3. 以至少获取内存顺序读取 `specptr` 字段。
    4. 如果 `specptr` 为 NULL，则 `initial_invoke` 指针不能依赖于 `specptr` 来保证正确执行。因此，`invoke` 不是 NULL，`specsigflags` 可以视为 0b00，`specptr` 可以视为 NULL。
    5. 如果 `specptr` 不是 null，那么 `initial_invoke` 可能不是使用 `specptr` 的最终 `invoke` 字段。这种情况可能发生在 `specptr` 已被写入，但 `invoke` 尚未被写入。因此，在 `specsigflags` 的第二位上自旋，直到它以至少获取内存顺序被设置为 1。
    6. 重新读取 `invoke` 字段，至少使用获取内存顺序。此加载将被称为 `final_invoke`。
    7. 读取 `specsigflags` 字段时可以使用任何内存顺序。
    8. `invoke` 是 `final_invoke`，`specsigflags` 是在第 7 步中读取的值，`specptr` 是在第 3 步中读取的值。
3. 当将 `specptr` 更新为不同但等效的函数指针时：

    1. 执行对新函数指针的释放存储到 `specptr`。这里的竞争条件必须是良性的，因为旧的函数指针仍然需要保持有效，并且任何新的指针也必须保持有效。一旦指针被写入 `specptr`，无论其是否被后续覆盖，它都必须始终可调用。

尽管这些写、读和更新步骤很复杂，但它们确保了 JIT 可以在不使现有 codeinsts 无效的情况下更新 codeinsts，并且 JIT 可以在不使现有 `invoke` 指针无效的情况下更新 codeinsts。这使得 JIT 在未来有可能以更高的优化级别重新优化函数，并且还将允许 JIT 在未来支持函数的并发编译。
