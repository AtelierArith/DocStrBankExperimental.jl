# Sanitizer support

[Sanitizers](https://github.com/google/sanitizers) 可以在自定义 Julia 构建中使用，以便更容易地检测 Julia 内部 C/C++ 代码中的某些类型的错误。

## Address Sanitizer: easy build

从Julia的源代码检出中，您应该能够构建一个支持Julia和LLVM中的地址清理的版本，如下所示：

```sh
$ mkdir /tmp/julia
$ contrib/asan/build.sh /tmp/julia/
```

在这里，我们选择了 `/tmp/julia` 作为构建目录，但您可以选择任何您想要的目录。构建完成后，使用 `/tmp/julia/julia` 运行您希望测试的工作负载。内存错误将导致错误。

如果您需要自定义或进一步的细节，请参阅下面的文档。

## General considerations

使用 Clang 的 sanitizers 显然需要你使用 Clang (`USECLANG=1`)，但还有另一个问题：大多数 sanitizers 需要一个运行时库，由主机编译器提供，而 Julia 的 JIT 生成的插装代码依赖于该库的功能。这意味着你的主机编译器的 LLVM 版本必须与 Julia 中使用的 LLVM 库的版本匹配。

一个简单的解决方案是拥有一个专用的构建文件夹，以提供匹配的工具链，通过使用 `BUILD_LLVM_CLANG=1` 进行构建。然后，您可以通过在覆盖 `CC` 和 `CXX` 变量时指定 `USECLANG=1`，从另一个构建文件夹引用此工具链。

当检测到使用 `RTLD_DEEPBIND` 打开的共享库时，清理工具会出错（参考：[google/sanitizers#611](https://github.com/google/sanitizers/issues/611)）。由于默认情况下 [libblastrampoline](https://github.com/staticfloat/libblastrampoline) 使用 `RTLD_DEEPBIND`，因此在使用清理工具时，我们需要设置环境变量 `LBT_USE_RTLD_DEEPBIND=0`。

要使用其中一个清理工具，请设置 `SANITIZE=1`，然后添加您想要使用的清理工具的相应标志。

在 macOS 上，这可能还需要一些额外的标志才能正常工作。总的来说，它可能看起来像这样，加上一个或多个下面列出的 `SANITIZE_*` 标志：

```
make -C deps USE_BINARYBUILDER_LLVM=0 LLVM_VER=svn stage-llvm

make -C src SANITIZE=1 USECLANG=1 \
    CC=~+/deps/scratch/llvm-svn/build_Release/bin/clang \
    CXX=~+/deps/scratch/llvm-svn/build_Release/bin/clang++ \
    CPPFLAGS="-isysroot $(xcode-select -p)/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk" \
    CXXFLAGS="-isystem $(xcode-select -p)/Toolchains/XcodeDefault.xctoolchain/usr/include/c++/v1"
```

（或将这些放入您的 `Make.user` 中，这样您就不需要每次都记住它们）。

## Address Sanitizer (ASAN)

为了检测或调试内存错误，您可以使用 Clang 的 [address sanitizer (ASAN)](https://clang.llvm.org/docs/AddressSanitizer.html)。通过使用 `SANITIZE_ADDRESS=1` 编译，您可以为 Julia 编译器及其生成的代码启用 ASAN。此外，您还可以指定 `LLVM_SANITIZE=1` 来清理 LLVM 库。请注意，这些选项会带来较高的性能和内存开销。例如，使用 ASAN 进行 Julia 和 LLVM 的测试使得 `testall1` 的运行时间增加 8-10 倍，同时内存使用量增加 20 倍（通过使用下面描述的选项，这些值可以分别减少到 3 倍和 4 倍）。

默认情况下，Julia 设置 `allow_user_segv_handler=1` ASAN 标志，这是信号传递正常工作的必要条件。您可以使用 `ASAN_OPTIONS` 环境标志定义其他选项，在这种情况下，您需要重复之前提到的默认选项。例如，通过指定 `fast_unwind_on_malloc=0` 和 `malloc_context_size=2` 可以减少内存使用，但会牺牲回溯的准确性。目前，Julia 还设置了 `detect_leaks=0`，但这应该在未来移除。

### Example setup

#### Step 1: Install toolchain

在 `$TOOLCHAIN_WORKTREE` 检出一个 Git 工作树（或创建一个树外构建目录），并创建一个配置文件 `$TOOLCHAIN_WORKTREE/Make.user`，内容为

```
USE_BINARYBUILDER_LLVM=1
BUILD_LLVM_CLANG=1
```

运行：

```sh
cd $TOOLCHAIN_WORKTREE
make -C deps install-llvm install-clang install-llvm-tools
```

将工具链二进制文件安装到 `$TOOLCHAIN_WORKTREE/usr/tools`

#### Step 2: Build Julia with ASAN

在 `$BUILD_WORKTREE` 检出一个 Git 工作树（或创建一个树外构建目录），并创建一个配置文件 `$BUILD_WORKTREE/Make.user`，内容为

```
TOOLCHAIN=$(TOOLCHAIN_WORKTREE)/usr/tools

# use our new toolchain
USECLANG=1
override CC=$(TOOLCHAIN)/clang
override CXX=$(TOOLCHAIN)/clang++
export ASAN_SYMBOLIZER_PATH=$(TOOLCHAIN)/llvm-symbolizer

USE_BINARYBUILDER_LLVM=1

override SANITIZE=1
override SANITIZE_ADDRESS=1

# make the GC use regular malloc/frees, which are hooked by ASAN
override WITH_GC_DEBUG_ENV=1

# default to a debug build for better line number reporting
override JULIA_BUILD_MODE=debug

# make ASAN consume less memory
export ASAN_OPTIONS=detect_leaks=0:fast_unwind_on_malloc=0:allow_user_segv_handler=1:malloc_context_size=2

JULIA_PRECOMPILE=1

# tell libblastrampoline to not use RTLD_DEEPBIND
export LBT_USE_RTLD_DEEPBIND=0
```

运行：

```sh
cd $BUILD_WORKTREE
make debug
```

构建 `julia-debug` 并使用 ASAN。

## Memory Sanitizer (MSAN)

为了检测未初始化内存的使用，您可以使用 Clang 的 [memory sanitizer (MSAN)](https://clang.llvm.org/docs/MemorySanitizer.html)，通过使用 `SANITIZE_MEMORY=1` 进行编译。

## Thread Sanitizer (TSAN)

为了调试数据竞争和其他与线程相关的问题，您可以使用 Clang 的 [thread sanitizer (TSAN)](https://clang.llvm.org/docs/ThreadSanitizer.html)，通过使用 `SANITIZE_THREAD=1` 进行编译。
