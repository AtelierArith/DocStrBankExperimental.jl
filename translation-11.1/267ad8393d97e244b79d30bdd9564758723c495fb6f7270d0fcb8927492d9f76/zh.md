# System Image Building

## [Building the Julia system image](@id Building-the-Julia-system-image)

Julia 附带一个预解析的系统映像，其中包含 `Base` 模块的内容，名为 `sys.ji`。该文件还被预编译成一个共享库，称为 `sys.{so,dll,dylib}`，以尽可能多的平台提供显著改善的启动时间。在不附带预编译系统映像文件的系统上，可以从 Julia 的 `DATAROOTDIR/julia/base` 文件夹中提供的源文件生成一个。

Julia 默认会在可用系统线程的一半上生成其系统映像。这可以通过 [`JULIA_IMAGE_THREADS`](@ref JULIA_IMAGE_THREADS) 环境变量进行控制。

此操作有多种用途。用户可以：

  * 在未随附预编译共享库系统映像的平台上构建一个，从而提高启动时间。
  * 修改 `Base`，重建系统映像，并在下次启动 Julia 时使用新的 `Base`。
  * 包含一个 `userimg.jl` 文件，该文件将包包含到系统映像中，从而创建一个在启动环境中嵌入包的系统映像。

[`PackageCompiler.jl` package](https://github.com/JuliaLang/PackageCompiler.jl) 包含方便的包装函数来自动化这个过程。

## [System image optimized for multiple microarchitectures](@id sysimg-multi-versioning)

系统映像可以在相同的指令集架构（ISA）下同时为多个CPU微架构编译。可以创建同一函数的多个版本，并在共享函数中插入最小调度点，以利用不同的ISA扩展或其他微架构特性。将在运行时根据可用的CPU特性自动选择提供最佳性能的版本。

### Specifying multiple system image targets

一个多微架构系统映像可以通过在系统映像编译期间传递多个目标来启用。这可以通过 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) make 选项或在手动运行编译命令时使用 `-C` 命令行选项来完成。多个目标在选项字符串中用 `;` 分隔。每个目标的语法是一个 CPU 名称，后面跟着多个用 `,` 分隔的特性。LLVM 支持的所有特性都被支持，并且可以使用 `-` 前缀禁用某个特性。（`+` 前缀也被允许，并且为了与 LLVM 语法一致而被忽略）。此外，还支持一些特殊特性来控制函数克隆行为。

!!! note
    对于除了第一个目标之外的每个目标，指定 `clone_all` 或 `base(<n>)` 是一个良好的实践。这使得哪些目标具有所有函数的克隆，以及哪些目标是基于其他目标变得明确。如果不这样做，默认行为是不克隆每个函数，并在不克隆函数时使用第一个目标的函数定义作为后备。


1. `克隆所有`

    默认情况下，只有最有可能受益于微架构特性的函数会被克隆。然而，当为目标指定 `clone_all` 时，系统映像中的 **所有** 函数将被克隆到该目标。负形式 `-clone_all` 可用于防止内置启发式方法克隆所有函数。
2. `base(<n>)`

    其中 `<n>` 是一个非负数的占位符（例如 `base(0)`，`base(1)`）。默认情况下，部分克隆的（即不是 `clone_all`）目标将在未克隆函数时使用默认目标（第一个指定的目标）中的函数。可以通过使用 `base(<n>)` 选项指定不同的基准来更改此行为。第 `n` 个目标（基于 0 的索引）将被用作基准目标，而不是默认的（第 `0` 个）目标。基准目标必须是 `0` 或另一个 `clone_all` 目标。将非 `clone_all` 目标指定为基准目标将导致错误。
3. `opt_size`

    这导致目标的函数在没有显著运行时性能影响时被优化为大小。这对应于 `-Os` GCC 和 Clang 选项。
4. `最小大小`

    这会导致目标函数被优化为可能对运行时性能产生显著影响的大小。这对应于 `-Oz` Clang 选项。

作为示例，在撰写本文时，以下字符串用于创建可从 julialang.org 下载的官方 `x86_64` Julia 二进制文件：

```
generic;sandybridge,-xsaveopt,clone_all;haswell,-rdrnd,base(1)
```

这创建了一个系统映像，包含三个独立的目标；一个用于通用的 `x86_64` 处理器，一个具有 `sandybridge` ISA（明确排除 `xsaveopt`）并显式克隆所有函数，另一个针对 `haswell` ISA，基于 `sandybridge` sysimg 版本，并且也排除 `rdrnd`。当 Julia 实现加载生成的 sysimg 时，它会检查主机处理器的 CPU 能力标志，以启用最高的 ISA 级别。请注意，基础级别（`generic`）需要 `cx16` 指令，该指令在某些虚拟化软件中被禁用，必须启用才能加载 `generic` 目标。或者，可以生成一个目标为 `generic,-cx16` 的 sysimg，以获得更好的兼容性，但请注意，这可能会导致某些代码的性能和稳定性问题。

### Implementation overview

这是实施中涉及的不同部分的简要概述。有关每个组件的更多实施细节，请参阅代码注释。

1. 系统映像编译

    解析和克隆决策在 `src/processor*` 中完成。我们目前支持基于循环、SIMD 指令或其他数学操作（例如 fastmath、fma、muladd）的函数克隆。此信息传递给 `src/llvm-multiversioning.cpp`，该文件执行实际的克隆。除了进行克隆和插入调度槽（有关如何执行此操作，请参见 `MultiVersioning::runOnModule` 中的注释）之外，该传递还生成元数据，以便运行时可以正确加载和初始化系统映像。有关元数据的详细描述，请参见 `src/processor.h`。
2. 系统映像加载

    系统映像的加载和初始化是在 `src/processor*` 中通过解析在系统映像生成期间保存的元数据完成的。主机特性检测和选择决策是在 `src/processor_*.cpp` 中根据 ISA 进行的。目标选择将优先考虑精确的 CPU 名称匹配、更大的向量寄存器大小和更多的特性。此过程的概述在 `src/processor.cpp` 中。
