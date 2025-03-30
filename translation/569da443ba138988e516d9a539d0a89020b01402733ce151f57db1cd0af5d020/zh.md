# Building Julia (Detailed)

## Downloading the Julia source code

如果您在防火墙后面，您可能需要使用 `https` 协议而不是 `git` 协议：

```sh
git config --global url."https://".insteadOf git://
```

确保还要配置系统以使用适当的代理设置，例如通过设置 `https_proxy` 和 `http_proxy` 变量。

## Building Julia

当第一次编译时，构建将自动下载预构建的 [external dependencies](#Required-Build-Tools-and-External-Libraries)。如果您更喜欢自己构建所有依赖项，或者在构建过程中无法访问网络的系统上进行构建，请在 `Make.user` 中添加以下内容：

```
USE_BINARYBUILDER=0
```

构建 Julia 需要 5GiB 的空间用于构建所有依赖项，以及大约 4GiB 的虚拟内存。

要执行并行构建，请使用 `make -j N` 并提供最大并发进程数。如果构建中的默认设置不适合您，并且您需要设置特定的 make 参数，可以将它们保存在 `Make.user` 中，并将该文件放置在您的 Julia 源代码根目录中。构建将自动检查 `Make.user` 的存在，并在其存在时使用它。

您可以通过在命令行中指定 `make O=<build-directory> configure` 来创建 Julia 的外部构建。这将在指定的目录中创建一个目录镜像，包含构建 Julia 所需的所有 Makefile。这些构建将共享 Julia 中的源文件和 `deps/srccache`。每个外部构建目录可以拥有自己的 `Make.user` 文件，以覆盖顶层文件夹中的全球 `Make.user` 文件。

如果一切正常，您将看到一个 Julia 横幅和一个交互式提示，您可以在其中输入要评估的表达式。（与库相关的错误可能是由于旧的、不兼容的库在您的 PATH 中存在。在这种情况下，请尝试将 `julia` 目录移动到 PATH 的前面）。请注意，上述大多数说明适用于 unix 系统。

要从任何地方运行 Julia，您可以：

  * 添加别名（在 `bash` 中：`echo "alias julia='/path/to/install/folder/bin/julia'" >> ~/.bashrc && source ~/.bashrc`），或者
  * 在 `julia` 目录中将 `julia` 可执行文件的软链接添加到 `/usr/local/bin`（或您路径中任何合适的目录），或者
  * 将 `julia` 目录添加到您此 shell 会话的可执行路径中（在 `bash` 中：`export PATH="$(pwd):$PATH"`；在 `csh` 或 `tcsh` 中：

`set path= ( $path $cwd )` ), 或者

  * 将 `julia` 目录永久添加到您的可执行路径中（例如，在 `.bash_profile` 中），或者
  * 将 `prefix=/path/to/install/folder` 写入 `Make.user`，然后运行 `make install`。如果该文件夹中已经安装了 Julia 的版本，您应该在运行 `make install` 之前将其删除。

一些可以设置以控制 Julia 构建的选项在文件 `Make.inc` 的开头列出并进行了文档说明，但您不应为此目的编辑它，而应使用 `Make.user`。

Julia的Makefile定义了方便的自动规则，称为`print-<VARNAME>`，用于打印变量的值，将`<VARNAME>`替换为要打印值的变量名称。例如

```console
$ make print-JULIA_PRECOMPILE
JULIA_PRECOMPILE=1
```

这些规则对于调试目的很有用。

现在你应该能够像这样运行 Julia：

```
julia
```

如果您正在为 Linux、macOS 或 Windows 构建 Julia 包，请查看 [distributing.md](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/distributing.md) 中的详细说明。

## Updating an existing source tree

如果您之前使用 `git clone` 下载了 `julia`，您可以使用 `git pull` 更新现有的源代码树，而不是重新开始：

```sh
cd julia
git pull && make
```

假设您没有对源树进行任何更改，这些更改将与上游更新冲突，这些命令将触发构建以更新到最新版本。

## General troubleshooting

1. 随着时间的推移，基础库可能会积累足够的更改，以至于构建系统映像的引导过程将失败。如果发生这种情况，构建可能会出现类似的错误：

    ```sh
     *** This error is usually fixed by running 'make clean'. If the error persists, try 'make cleanall' ***
    ```

    如上所述，运行 `make clean && make` 通常是足够的。偶尔，需要通过 `make cleanall` 进行更强的清理。
2. 新版本的外部依赖项可能会被引入，这可能偶尔会导致与旧版本现有构建的冲突。

    a. 特殊的 `make` 目标存在以帮助清除依赖项的现有构建。例如，`make -C deps clean-llvm` 将清除现有的 `llvm` 构建，以便在下次调用 `make` 时从下载的源分发版重新构建 `llvm`。`make -C deps distclean-llvm` 是一种更强的清除，它还会删除下载的源分发版，确保下次调用 `make` 时将下载源分发版的新副本，并应用任何新的补丁。

    b. 要删除现有的 `julia` 二进制文件及其所有依赖项，请删除 *源代码树* 中的 `./usr` 目录。
3. 如果您最近更新了 macOS，请确保运行 `xcode-select --install` 来更新命令行工具。否则，您可能会遇到缺少头文件和库的错误，例如 `ld: library not found for -lcrt1.10.6.o`。
4. 如果您已移动源目录，您可能会遇到错误，例如 `CMake Error: The current CMakeCache.txt directory ... is different than the directory ... where CMakeCache.txt was created.`，在这种情况下，您可以在 `deps` 下删除有问题的依赖项。
5. 在极端情况下，您可能希望将源树重置为原始状态。以下 git 命令可能会有所帮助：

    ```sh
     git reset --hard #Forcibly remove any changes to any files under version control
     git clean -x -f -d #Forcibly remove any file or directory not under version control
    ```

    *为了避免丢失工作，请确保在运行这些命令之前了解它们的作用。`git` 将无法撤销这些更改！*

## Platform-Specific Notes

各种操作系统的笔记：

  * [Linux](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/linux.md)
  * [macOS](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/macos.md)
  * [Windows](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/windows.md)
  * [FreeBSD](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/freebsd.md)

各种架构的笔记：

  * [ARM](https://github.com/JuliaLang/julia/blob/master/doc/src/devdocs/build/arm.md)

## Required Build Tools and External Libraries

构建 Julia 需要安装以下软件：

  * **[GNU make]**                — 构建依赖关系。
  * **[gcc & g++][gcc]** (>= 7.1) 或 **[Clang][clang]** (>= 5.0, >= 9.3 适用于 Apple Clang) — 编译和链接 C, C++。
  * **[libatomic][gcc]**          — 由 **[gcc]** 提供，支持原子操作所需。
  * **[python]** (>=2.7)          — 需要构建 LLVM。
  * **[gfortran]**                — 编译和链接 Fortran 库。
  * **[perl]**                    — 库头文件的预处理。
  * **[wget]**、**[curl]** 或 **[fetch]**（FreeBSD）— 自动下载外部库。
  * **[m4]**                      — 构建 GMP 所需。
  * **[awk]**                     — Makefile 的辅助工具。
  * **[补丁]**                   — 用于修改源代码。
  * **[cmake]** (>= 3.4.3)        — 构建 `libgit2` 所需。
  * **[pkg-config]**              — 需要正确构建 `libgit2`，特别是为了支持代理。
  * **[powershell]** (>= 3.0)     — 仅在Windows上必要。
  * **[which]**                   — 用于检查构建依赖项。

在基于Debian的发行版（例如Ubuntu）上，您可以使用 `apt-get` 轻松安装它们：

```
sudo apt-get install build-essential libatomic1 python gfortran perl wget m4 cmake pkg-config curl
```

Julia 使用以下外部库，这些库会在您第一次运行 `make` 时自动下载（或在少数情况下，包含在 Julia 源代码库中）并从源代码编译。这些库的具体版本号在 [`deps/$(libname).version`](https://github.com/JuliaLang/julia/blob/master/deps/) 中列出：

  * **[LLVM]** (15.0 + [patches](https://github.com/JuliaLang/llvm-project/tree/julia-release/15.x)) — 编译器基础设施 (见 [note below](#llvm))。
  * **[FemtoLisp]**            — 随 Julia 源代码打包，并用于实现编译器前端。
  * **[libuv]**  (自定义分支) — 可移植的高性能事件驱动I/O库。
  * **[OpenLibm]**             — 可移植的 libm 库，包含基本数学函数。
  * **[DSFMT]**                — 快速梅森旋转伪随机数生成器库。
  * **[OpenBLAS]**             — 快速、开放且维护中的 [基本线性代数子程序 (BLAS)]
  * **[LAPACK]**               — 线性代数例程库，用于求解同时线性方程组、线性方程组的最小二乘解、特征值问题和奇异值问题。
  * **[MKL]** (可选)       – OpenBLAS 和 LAPACK 可以被英特尔的 MKL 库替代。
  * **[SuiteSparse]**          — 稀疏矩阵的线性代数例程库。
  * **[PCRE]**                 — 与Perl兼容的正则表达式库。
  * **[GMP]**                  — GNU 多重精度算术库，支持 `BigInt` 所需。
  * **[MPFR]**                 — GNU 多精度浮点库，支持任意精度浮点数 (`BigFloat`) 所需。
  * **[libgit2]**              — Git 可链接库，用于 Julia 的包管理器。
  * **[curl]**                 — libcurl 提供下载和代理支持。
  * **[libssh2]**              — 用于SSH传输的库，libgit2在使用SSH远程时使用该库。
  * **[mbedtls]**              — 用于加密和传输层安全的库，libssh2 使用它
  * **[utf8proc]**             — 一个用于处理UTF-8编码的Unicode字符串的库。
  * **[LLVM libunwind]** — LLVM 的 [libunwind] 分支，一个确定程序调用链的库。
  * **[ITTAPI]**               — 英特尔的仪器和追踪技术及即时API。

[GNU make]:     https://www.gnu.org/software/make [patch]:        https://www.gnu.org/software/patch [wget]:         https://www.gnu.org/software/wget [m4]:           https://www.gnu.org/software/m4 [awk]:          https://www.gnu.org/software/gawk [gcc]:          https://gcc.gnu.org [clang]:        https://clang.llvm.org [python]:       https://www.python.org/ [gfortran]:     https://gcc.gnu.org/fortran/ [curl]:         https://curl.haxx.se [fetch]:        https://www.freebsd.org/cgi/man.cgi?fetch(1) [perl]:         https://www.perl.org [cmake]:        https://www.cmake.org [OpenLibm]:     https://github.com/JuliaLang/openlibm [DSFMT]:        https://github.com/MersenneTwister-Lab/dSFMT [OpenBLAS]:     https://github.com/xianyi/OpenBLAS [LAPACK]:       https://www.netlib.org/lapack [MKL]:          https://software.intel.com/en-us/articles/intel-mkl [SuiteSparse]:  https://people.engr.tamu.edu/davis/suitesparse.html [PCRE]:         https://www.pcre.org [LLVM]:         https://www.llvm.org [LLVM libunwind]: https://github.com/llvm/llvm-project/tree/main/libunwind [FemtoLisp]:    https://github.com/JeffBezanson/femtolisp [GMP]:          https://gmplib.org [MPFR]:         https://www.mpfr.org [libuv]:        https://github.com/JuliaLang/libuv [libgit2]:      https://libgit2.org/ [utf8proc]:     https://julialang.org/utf8proc/ [libunwind]:    https://www.nongnu.org/libunwind [libssh2]:      https://www.libssh2.org [mbedtls]:      https://tls.mbed.org/ [pkg-config]:   https://www.freedesktop.org/wiki/Software/pkg-config/ [powershell]:   https://docs.microsoft.com/en-us/powershell/scripting/wmf/overview [which]:        https://carlowood.github.io/which/ [ITTAPI]:       https://github.com/intel/ittapi

## Build dependencies

如果您已经在系统上安装了一个或多个这些软件包，您可以通过将 `USE_SYSTEM_...=1` 传递给 `make` 或将该行添加到 `Make.user` 来防止 Julia 编译这些库的重复版本。所有可能的标志的完整列表可以在 `Make.inc` 中找到。

请注意，此过程并未得到官方支持，因为它会为依赖项的安装和版本引入额外的变数，仅建议系统软件包维护者使用。可能会出现意外的编译错误，因为构建系统不会进一步检查以确保安装了正确的软件包。

### LLVM

最复杂的依赖是LLVM，我们需要来自上游的额外补丁（LLVM不向后兼容）。

对于将Julia与LLVM打包，我们建议使用以下任一方法：

  * 将仅包含Julia的LLVM库打包到Julia包中，或者
  * 将补丁添加到发行版的LLVM包中。

      * 完整的补丁列表可在 [Github](https://github.com/JuliaLang/llvm-project) 中找到，请查看 `julia-release/15.x` 分支。
      * 唯一与Julia相关的补丁是库重命名（`llvm7-symver-jlprefix.patch`），该补丁*不应*应用于系统LLVM。
      * 剩余的补丁都是上游的错误修复，并已贡献到上游LLVM中。

使用未修补或不同版本的LLVM将导致错误和/或性能不佳。您可以通过在`Make.user`文件中使用以下选项，从远程Git仓库构建不同版本的LLVM：

```make
# Force source build of LLVM
USE_BINARYBUILDER_LLVM = 0
# Use Git for fetching LLVM source code
# this is either `1` to get all of them
DEPS_GIT = 1
# or a space-separated list of specific dependencies to download with git
DEPS_GIT = llvm

# Other useful options:
#URL of the Git repository you want to obtain LLVM from:
#  LLVM_GIT_URL = ...
#Name of the alternate branch to clone from git
#  LLVM_BRANCH = julia-16.0.6-0
#SHA hash of the alterate commit to check out automatically
#  LLVM_SHA1 = $(LLVM_BRANCH)
#List of LLVM targets to build.  It is strongly recommended to keep at least all the
#default targets listed in `deps/llvm.mk`, even if you don't necessarily need all of them.
#  LLVM_TARGETS = ...
#Use ccache for faster recompilation in case you need to restart a build.
#  USECCACHE = 1
#  CMAKE_GENERATOR=Ninja
#  LLVM_ASSERTIONS=1
#  LLVM_DEBUG=Symbols
```

各种构建阶段由特定文件控制：

  * `deps/llvm.version` : 触摸或更改以检出新版本，`make get-llvm check-llvm`
  * `deps/srccache/llvm/source-extracted` : `make extract-llvm` 的结果
  * `deps/llvm/build_Release*/build-configured` : `make configure-llvm` 的结果
  * `deps/llvm/build_Release*/build-configured` : `make compile-llvm` 的结果
  * `usr-staging/llvm/build_Release*.tgz` : `make stage-llvm` 的结果（使用 `make reinstall-llvm` 重新生成）
  * `usr/manifest/llvm` : `make install-llvm` 的结果（使用 `make uninstall-llvm` 重新生成）
  * `make version-check-llvm` : 每次运行时都会警告用户是否有本地修改

尽管Julia可以使用更新的LLVM版本构建，但对此的支持应视为实验性，不适合打包。

### libuv

Julia 使用了 libuv 的自定义分支。它是一个小型依赖项，可以安全地与 Julia 打包在同一个包中，并且不会与系统库冲突。Julia 构建不应尝试使用系统 libuv。

### BLAS and LAPACK

作为一种高性能数值语言，Julia 应该链接到多线程的 BLAS 和 LAPACK，例如 OpenBLAS 或 ATLAS，这将提供比某些系统上可能默认的参考 `libblas` 实现更好的性能。

## Source distributions of releases

每个 Julia 的预发布和发布都有一个“完整”的源代码分发和一个“轻量”的源代码分发。

完整的源代码分发版包含Julia的源代码及所有依赖项，以便可以在没有互联网连接的情况下从源代码构建。轻量级源代码分发版不包括依赖项的源代码。

例如，`julia-1.0.0.tar.gz` 是 Julia `v1.0.0` 版本的轻量源代码分发包，而 `julia-1.0.0-full.tar.gz` 是完整源代码分发包。

## Building Julia from source with a Git checkout of a stdlib

如果您需要从源代码构建 Julia，并且使用 stdlib 的 Git 检出版本，请在构建 Julia 时使用 `make DEPS_GIT=NAME_OF_STDLIB`。

例如，如果您需要从源代码构建 Julia，并且使用 Pkg 的 Git 检出版本，则在构建 Julia 时使用 `make DEPS_GIT=Pkg`。`Pkg` 仓库位于 `stdlib/Pkg`，最初是以分离的 `HEAD` 创建的。如果您是从一个已有的 Julia 仓库进行此操作，您可能需要提前执行 `make clean`。

如果您需要从源代码构建 Julia，并且需要多个标准库的 Git 检出，则 `DEPS_GIT` 应该是一个以空格分隔的标准库名称列表。例如，如果您需要从源代码构建 Julia，并且需要 Pkg、Tar 和 Downloads 的 Git 检出，则在构建 Julia 时使用 `make DEPS_GIT='Pkg Tar Downloads'`。

## Building an "assert build" of Julia

一个“assert build”是指在构建时同时使用了 `FORCE_ASSERTIONS=1` 和 `LLVM_ASSERTIONS=1`。要构建一个 assert build，请在您的 `Make.user` 文件中定义以下两个变量：

```
FORCE_ASSERTIONS=1
LLVM_ASSERTIONS=1
```

请注意，带有断言的 Julia 构建将比常规（非断言）构建慢。

## Building 32-bit Julia on a 64-bit machine

偶尔，特定于32位架构的错误可能会出现，当这种情况发生时，能够在本地机器上调试问题是很有用的。由于大多数现代64位系统支持运行为32位构建的程序，如果您不需要从源代码重新编译Julia（例如，您主要需要检查32位Julia的行为而不必接触C代码），您可以使用可以从[official downloads page](https://julialang.org/downloads/)获取的适用于您系统的32位版本的Julia。然而，如果您确实需要从源代码重新编译Julia，一个选项是使用32位系统的Docker容器。至少目前，使用[ubuntu 32-bit docker images](https://hub.docker.com/r/i386/ubuntu)构建32位版本的Julia相对简单。简而言之，在设置`docker`之后，以下是所需的步骤：

```sh
$ docker pull i386/ubuntu
$ docker run --platform i386 -i -t i386/ubuntu /bin/bash
```

在这一点上，您应该处于一个 32 位机器控制台（请注意，`uname` 报告主机架构，因此仍会显示 64 位，但这不会影响 Julia 的构建）。您可以添加包并编译代码；当您 `exit` 时，所有更改将会丢失，因此请确保在单个会话中完成您的分析，或者设置一个可复制/粘贴的脚本，以便您可以用来设置您的环境。

从这一点开始，你应该

```sh
# apt update
```

（请注意，`sudo` 并未安装，但由于您以 `root` 身份运行，因此也不需要它，因此可以从所有命令中省略 `sudo`。）

然后添加所有的 [build dependencies](#required-build-tools-and-external-libraries)，选择一个你喜欢的基于控制台的编辑器，`git`，以及你需要的其他任何工具（例如，`gdb`，`rr` 等）。选择一个工作目录并 `git clone` Julia，检出你希望调试的分支，并像往常一样构建 Julia。

## Update the version number of a dependency

有两种类型的构建

1. 从源代码构建所有内容（`deps/` 和 `src/`）。 （在 `Make.user` 中添加 `USE_BINARYBUILDER=0`，参见 [Building Julia](#building-julia)）
2. 从源代码（`src/`）构建，使用预编译的依赖项（默认）

当您想要更新 `deps/` 中依赖项的版本号时，您可能想要使用以下检查清单：

```md
### Check list

Version numbers:
- [ ] `deps/$(libname).version`: `LIBNAME_VER`, `LIBNAME_BRANCH`, `LIBNAME_SHA1` and `LIBNAME_JLL_VER`
- [ ] `stdlib/$(LIBNAME_JLL_NAME)_jll/Project.toml`: `version`

Checksum:
- [ ] `deps/checksums/$(libname)`
- [ ] `deps/checksums/$(LIBNAME_JLL_NAME)-*/`: `md5` and `sha512`

Patches:
- [ ] `deps/$(libname).mk`
- [ ] `deps/patches/$(libname)-*.patch`
```

注意：

  * 对于特定的依赖项，检查清单中的某些项目可能不存在。
  * 对于校验和文件，它可以是**一个没有后缀的单个文件**，或者**一个包含两个文件的文件夹**。

### Example: `OpenLibm`

1. 更新 `deps/openlibm.version` 中的版本号

      * `OPENLIBM_VER := 0.X.Y`
      * `OPENLIBM_BRANCH = v0.X.Y`
      * `OPENLIBM_SHA1 = new-sha1-hash`
2. 在 `stdlib/OpenLibm_jll/Project.toml` 中更新版本号

      * `version = "0.X.Y+0"`
3. 更新 `deps/checksums/openlibm` 中的校验和

      * `make -f contrib/refresh_checksums.mk openlibm`
4. 检查补丁文件 `deps/patches/openlibm-*.patch` 是否存在

      * 如果补丁不存在，则跳过。
      * 如果补丁存在，请检查它们是否已合并到新版本中并需要删除。删除补丁时，请记得修改相应的 Makefile 文件（`deps/openlibm.mk`）。
