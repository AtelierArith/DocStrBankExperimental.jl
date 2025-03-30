# [Package Images](@id pkgimages)

Julia 包 images 为 Julia 包提供对象（本机代码）缓存。它们类似于 Julia 的 [system image](@ref dev-sysimg)，并支持许多相同的功能。实际上，底层序列化格式是相同的，系统映像是包映像构建的基础映像。

## High-level overview

包图像是包含代码和数据的共享库。与 `.ji` 缓存文件类似，它们是按包生成的。数据部分包含全局数据（包中的全局变量）以及有关包定义的方法和类型的必要元数据。代码部分包含本机对象，这些对象缓存了 Julia 基于 LLVM 的编译器的最终输出。

命令行选项 `--pkgimages=no` 可用于关闭此会话的对象缓存。请注意，这意味着缓存文件可能需要重新生成。请参见 [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@ref JULIA_MAX_NUM_PRECOMPILE_FILES) 以获取 Julia 默认缓存的变体上限。

!!! note
    虽然包的图像表现得像本地共享库，但它们仅仅是对此的近似。您将无法从本地程序中链接它们，必须从Julia中加载它们。


## Linking

由于包图像包含本机代码，我们必须在使用它们之前对其运行链接器。您可以将环境变量 [`JULIA_VERBOSE_LINKING`](@ref JULIA_VERBOSE_LINKING) 设置为 `true` 以使包图像链接过程详细化。

此外，我们不能假设用户安装了一个可用的系统链接器。因此，Julia 随附 LLD，即 LLVM 链接器，以提供开箱即用的体验。在 `base/linking.jl` 中，我们实现了一个有限的接口，以便能够在所有支持的平台上链接包图像。

### Quirks

尽管LLD是一个多平台链接器，但它并未在各个平台之间提供一致的接口。此外，它旨在通过`clang`或其他编译器驱动程序使用，因此我们重新实现了部分来自`llvm-project/clang/lib/Driver/ToolChains`的逻辑。幸运的是，可以使用`lld -flavor`将lld设置为正确的平台。

#### Windows

为了避免处理 `link.exe`，我们使用 `-flavor gnu`，有效地将 `lld` 转变为来自 mingw32 环境的交叉链接器。Windows DLL 必须包含一个 `_DllMainCRTStartup` 函数，并且为了最小化我们对 mingw32 库的依赖，我们自己注入一个存根定义。

#### MacOS

在 macOS 上，动态库需要链接 `-lSystem`。在最近的 macOS 版本中，只有在 Xcode 可用时，`-lSystem` 才可以用于链接。为此，我们使用 `-undefined dynamic_lookup` 进行链接。

## [Package images optimized for multiple microarchitectures](@id pkgimgs-multi-versioning)

类似于 [multi-versioning](@ref sysimg-multi-versioning) 的系统镜像，包镜像支持多版本。如果您处于异构环境中，并且有统一的缓存，您可以设置环境变量 `JULIA_CPU_TARGET=generic` 来对对象缓存进行多版本管理。

## Flags that impact package image creation and selection

这些是影响缓存选择的 Julia 命令行标志。使用不同标志创建的包图像将被拒绝。

  * `-g`，`--debug-info`：需要精确匹配，因为它会改变代码生成。
  * `--check-bounds`: 由于它会改变代码生成，因此需要精确匹配。
  * `--inline`: 需要精确匹配，因为它会改变代码生成。
  * `--pkgimages`: 允许在未启用对象缓存的情况下运行。
  * `-O`，`--optimize`：拒绝为较低优化级别生成的包图像，但允许加载较高优化级别的图像。
