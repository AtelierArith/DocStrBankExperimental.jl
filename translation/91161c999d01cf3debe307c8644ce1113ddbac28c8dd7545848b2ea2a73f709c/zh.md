# Environment Variables

Julia 可以通过多种环境变量进行配置，这些变量可以按照每个操作系统的常规方式设置，也可以通过 Julia 内部以可移植的方式设置。假设您想将环境变量 [`JULIA_EDITOR`](@ref JULIA_EDITOR) 设置为 `vim`，您可以输入 `ENV["JULIA_EDITOR"] = "vim"`（例如，在 REPL 中）来逐个进行更改，或者将相同的内容添加到用户主目录中的用户配置文件 `~/.julia/config/startup.jl` 中，以便产生永久效果。可以通过评估 `ENV["JULIA_EDITOR"]` 来确定该环境变量的当前值。

Julia 使用的环境变量通常以 `JULIA` 开头。如果调用 [`InteractiveUtils.versioninfo`](@ref) 并使用关键字 `verbose=true`，则输出将列出与 Julia 相关的任何已定义环境变量，包括那些名称中包含 `JULIA` 的变量。

!!! note
    建议避免在运行时更改环境变量，例如在 `~/.julia/config/startup.jl` 中。

    一个原因是某些 Julia 语言变量，例如 [`JULIA_NUM_THREADS`](@ref JULIA_NUM_THREADS) 和 [`JULIA_PROJECT`](@ref JULIA_PROJECT)，需要在 Julia 启动之前设置。

    同样，sysimage 中用户模块的 `__init__()` 函数（通过 PackageCompiler）在 `startup.jl` 之前运行，因此在 `startup.jl` 中设置环境变量可能对用户代码来说为时已晚。

    此外，在运行时更改环境变量可能会在原本无害的代码中引入数据竞争。

    在 Bash 中，环境变量可以通过手动运行，例如在启动 Julia 之前运行 `export JULIA_NUM_THREADS=4` 来设置，或者通过将相同的命令添加到 `~/.bashrc` 或 `~/.bash_profile` 中，以便每次启动 Bash 时设置该变量。


## File locations

### [`JULIA_BINDIR`](@id JULIA_BINDIR)

包含 Julia 可执行文件的目录的绝对路径，该路径设置全局变量 [`Sys.BINDIR`](@ref)。如果未设置 `$JULIA_BINDIR`，则 Julia 在运行时确定 `Sys.BINDIR` 的值。

可执行文件本身是其中之一

```
$JULIA_BINDIR/julia
$JULIA_BINDIR/julia-debug
```

默认情况下。

全局变量 `Base.DATAROOTDIR` 确定了从 `Sys.BINDIR` 到与 Julia 相关的数据目录的相对路径。然后路径

```
$JULIA_BINDIR/$DATAROOTDIR/julia/base
```

确定Julia最初搜索源文件的目录（通过`Base.find_source_file()`）。

同样，全球变量 `Base.SYSCONFDIR` 确定了配置文件目录的相对路径。然后，Julia 会在以下位置搜索 `startup.jl` 文件：

```
$JULIA_BINDIR/$SYSCONFDIR/julia/startup.jl
$JULIA_BINDIR/../etc/julia/startup.jl
```

默认情况下（通过 `Base.load_julia_startup()`）。

例如，一个Linux安装，其中Julia可执行文件位于`/bin/julia`，`DATAROOTDIR`为`../share`，`SYSCONFDIR`为`../etc`，将会有[`JULIA_BINDIR`](@ref JULIA_BINDIR)设置为`/bin`，源文件搜索路径为

```
/share/julia/base
```

和全局配置搜索路径为

```
/etc/julia/startup.jl
```

### [`JULIA_PROJECT`](@id JULIA_PROJECT)

一个目录路径，指示哪个项目应该是初始活动项目。设置此环境变量的效果与指定 `--project` 启动选项相同，但 `--project` 的优先级更高。如果变量设置为 `@.`（注意尾随的点），则 Julia 会尝试从当前目录及其父目录中查找包含 `Project.toml` 或 `JuliaProject.toml` 文件的项目目录。另请参阅关于 [Code Loading](@ref code-loading) 的章节。

!!! note
    [`JULIA_PROJECT`](@ref JULIA_PROJECT) 必须在启动 Julia 之前定义；在 `startup.jl` 中定义是在启动过程中太晚了。


### [`JULIA_LOAD_PATH`](@id JULIA_LOAD_PATH)

[`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) 环境变量用于填充全局 Julia [`LOAD_PATH`](@ref) 变量，该变量决定可以通过 `import` 和 `using` 加载哪些包（参见 [Code Loading](@ref code-loading)）。

与 shell 的 `PATH` 变量不同，[`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) 中的空条目在填充 `LOAD_PATH` 时会扩展为默认值 `LOAD_PATH`，即 `["@", "@v#.#", "@stdlib"]`。这使得在 shell 脚本中，无论 `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` 是否已经设置，都可以轻松地附加、前置等加载路径值。例如，要将目录 `/foo/bar` 前置到 `LOAD_PATH`，只需执行

```sh
export JULIA_LOAD_PATH="/foo/bar:$JULIA_LOAD_PATH"
```

如果 [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) 环境变量已经设置，则其旧值将被添加前缀 `/foo/bar`。另一方面，如果 `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` 未设置，则它将被设置为 `/foo/bar:`，这将扩展为 `LOAD_PATH` 值 `["/foo/bar", "@", "@v#.#", "@stdlib"]`。如果 `4d61726b646f776e2e436f64652822222c20224a554c49415f4c4f41445f504154482229_40726566204a554c49415f4c4f41445f50415448` 被设置为空字符串，则它扩展为一个空的 `LOAD_PATH` 数组。换句话说，空字符串被解释为一个零元素数组，而不是一个包含空字符串的单元素数组。选择这种行为是为了能够通过环境变量设置一个空的加载路径。如果您想要默认的加载路径，可以取消设置环境变量，或者如果必须有一个值，则将其设置为字符串 `:`。

!!! note
    在 Windows 上，路径元素由 `;` 字符分隔，这与 Windows 上的大多数路径列表相同。


### [`JULIA_DEPOT_PATH`](@id JULIA_DEPOT_PATH)

[`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 环境变量用于填充全局 Julia [`DEPOT_PATH`](@ref) 变量，该变量控制包管理器以及 Julia 的代码加载机制查找包注册表、已安装的包、命名环境、仓库克隆、缓存的编译包镜像、配置文件和 REPL 历史文件的默认位置。

与 shell 的 `PATH` 变量不同，但与 [`JULIA_LOAD_PATH`](@ref JULIA_LOAD_PATH) 类似，[`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 中的空条目具有特殊行为：

  * 最后，它扩展为 `DEPOT_PATH` 的默认值，*不包括* 用户仓库。
  * 在开始时，它被扩展为 `DEPOT_PATH` 的默认值，*包括* 用户仓库。

这允许轻松覆盖用户仓库，同时仍然保留对与 Julia 捆绑的资源的访问，例如缓存文件、工件等。例如，要将用户仓库切换到 `/foo/bar`，请使用尾随的 `:`。

```sh
export JULIA_DEPOT_PATH="/foo/bar:"
```

所有包操作，如克隆注册表或安装包，现在将写入 `/foo/bar`，但由于空条目被扩展为默认系统仓库，任何捆绑资源仍然可用。如果您确实只想使用 `/foo/bar` 中的仓库，而不加载任何捆绑资源，只需将环境变量设置为 `/foo/bar`，而不带尾部冒号。

要在完整的默认列表末尾添加一个仓库，包括默认用户仓库，请使用前导 `:`

```sh
export JULIA_DEPOT_PATH=":/foo/bar"
```

有两个例外情况。首先，如果 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 被设置为空字符串，它会扩展为一个空的 `DEPOT_PATH` 数组。换句话说，空字符串被解释为一个零元素数组，而不是一个包含空字符串的单元素数组。选择这种行为是为了能够通过环境变量设置一个空的仓库路径。

其次，如果在 [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 中未指定用户仓库，则空条目将扩展为默认仓库 *包括* 用户仓库。这使得通过将环境变量设置为字符串 `:`，可以像未设置环境变量一样使用默认仓库。

!!! note
    在Windows上，路径元素由 `;` 字符分隔，这与Windows上的大多数路径列表相同。


!!! note
    [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) 必须在启动 Julia 之前定义；在 `startup.jl` 中定义为时已晚；此时你可以直接修改 `DEPOT_PATH` 数组，该数组是从环境变量中填充的。


### [`JULIA_HISTORY`](@id JULIA_HISTORY)

REPL 的历史文件的绝对路径 `REPL.find_hist_file()`。如果未设置 `$JULIA_HISTORY`，则 `REPL.find_hist_file()` 默认为

```
$(DEPOT_PATH[1])/logs/repl_history.jl
```

### [`JULIA_MAX_NUM_PRECOMPILE_FILES`](@id JULIA_MAX_NUM_PRECOMPILE_FILES)

设置要存储在预编译缓存中的单个软件包的最大不同实例数量（默认值 = 10）。

### [`JULIA_VERBOSE_LINKING`](@id JULIA_VERBOSE_LINKING)

如果设置为 true，链接器命令将在预编译期间显示。

## Pkg.jl

### [`JULIA_CI`](@id JULIA_CI)

如果设置为 `true`，这表示给包服务器，任何包操作都是持续集成（CI）系统的一部分，目的是收集包使用统计信息。

### [`JULIA_NUM_PRECOMPILE_TASKS`](@id JULIA_NUM_PRECOMPILE_TASKS)

用于预编译包时使用的并行任务数量。请参见 [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile)。

### [`JULIA_PKG_DEVDIR`](@id JULIA_PKG_DEVDIR)

[`Pkg.develop`](https://pkgdocs.julialang.org/v1/api/#Pkg.develop) 用于下载包的默认目录。

### [`JULIA_PKG_IGNORE_HASHES`](@id JULIA_PKG_IGNORE_HASHES)

如果设置为 `1`，这将忽略工件中的不正确哈希值。应谨慎使用，因为这会禁用下载的验证，但在跨不同类型的文件系统移动文件时可以解决问题。有关更多详细信息，请参见 [Pkg.jl issue #2317](https://github.com/JuliaLang/Pkg.jl/issues/2317)。

!!! compat "Julia 1.6"
    这仅在 Julia 1.6 及以上版本中受支持。


### [`JULIA_PKG_OFFLINE`](@id JULIA_PKG_OFFLINE)

如果设置为 `true`，这将启用离线模式：见 [`Pkg.offline`](https://pkgdocs.julialang.org/v1/api/#Pkg.offline)。

!!! compat "Julia 1.5"
    Pkg的离线模式需要Julia 1.5或更高版本。


### [`JULIA_PKG_PRECOMPILE_AUTO`](@id JULIA_PKG_PRECOMPILE_AUTO)

如果设置为 `0`，这将禁用由更改清单的包操作自动预编译。请参见 [`Pkg.precompile`](https://pkgdocs.julialang.org/v1/api/#Pkg.precompile)。

### [`JULIA_PKG_SERVER`](@id JULIA_PKG_SERVER)

指定要使用的包注册表的 URL。默认情况下，`Pkg` 使用 `https://pkg.julialang.org` 来获取 Julia 包。此外，您可以禁用 PkgServer 协议的使用，而是通过设置：`export JULIA_PKG_SERVER=""` 直接从其主机（GitHub、GitLab 等）访问包。

### [`JULIA_PKG_SERVER_REGISTRY_PREFERENCE`](@id JULIA_PKG_SERVER_REGISTRY_PREFERENCE)

指定首选的注册表风格。目前支持的值为 `conservative`（默认值），它只会发布已由存储服务器处理的资源（因此更有可能从 PkgServers 获得），而 `eager` 则会发布那些资源不一定经过存储服务器处理的注册表。处于限制性防火墙后且不允许从任意服务器下载的用户不应使用 `eager` 风格。

!!! compat "Julia 1.7"
    这仅影响 Julia 1.7 及以上版本。


### [`JULIA_PKG_UNPACK_REGISTRY`](@id JULIA_PKG_UNPACK_REGISTRY)

如果设置为 `true`，这将解压注册表，而不是将其存储为压缩的 tarball。

!!! compat "Julia 1.7"
    这仅影响 Julia 1.7 及以上版本。早期版本将始终解压注册表。


### [`JULIA_PKG_USE_CLI_GIT`](@id JULIA_PKG_USE_CLI_GIT)

如果设置为 `true`，则使用 git 协议的 Pkg 操作将使用外部 `git` 可执行文件，而不是默认的 libgit2 库。

!!! compat "Julia 1.7"
    使用 `git` 可执行文件仅支持 Julia 1.7 及以上版本。


### [`JULIA_PKGRESOLVE_ACCURACY`](@id JULIA_PKGRESOLVE_ACCURACY)

包解析器的准确性。这应该是一个正整数，默认值为 `1`。

### [`JULIA_PKG_PRESERVE_TIERED_INSTALLED`](@id JULIA_PKG_PRESERVE_TIERED_INSTALLED)

将默认的包安装策略更改为 `Pkg.PRESERVE_TIERED_INSTALLED`，以便让包管理器在尽可能保留已安装的多个版本的情况下尝试安装包的版本。

!!! compat "Julia 1.9"
    这仅影响 Julia 1.9 及以上版本。


## Network transport

### [`JULIA_NO_VERIFY_HOSTS`](@id JULIA_NO_VERIFY_HOSTS)

### [`JULIA_SSL_NO_VERIFY_HOSTS`](@id JULIA_SSL_NO_VERIFY_HOSTS)

### [`JULIA_SSH_NO_VERIFY_HOSTS`](@id JULIA_SSH_NO_VERIFY_HOSTS)

### [`JULIA_ALWAYS_VERIFY_HOSTS`](@id JULIA_ALWAYS_VERIFY_HOSTS)

指定应验证或不应验证特定传输层的主机身份。请参见 [`NetworkOptions.verify_host`](https://github.com/JuliaLang/NetworkOptions.jl#verify_host)

### [`JULIA_SSL_CA_ROOTS_PATH`](@id JULIA_SSL_CA_ROOTS_PATH)

指定包含证书颁发机构根证书的文件或目录。请参见 [`NetworkOptions.ca_roots`](https://github.com/JuliaLang/NetworkOptions.jl#ca_roots)

## External applications

### [`JULIA_SHELL`](@id JULIA_SHELL)

Julia 执行外部命令时使用的 shell 的绝对路径（通过 `Base.repl_cmd()`）。默认为环境变量 `$SHELL`，如果 `$SHELL` 未设置，则回退到 `/bin/sh`。

!!! note
    在Windows上，此环境变量被忽略，外部命令直接执行。


### [`JULIA_EDITOR`](@id JULIA_EDITOR)

由 `InteractiveUtils.editor()` 返回的编辑器，例如在 [`InteractiveUtils.edit`](@ref) 中使用，指的是首选编辑器的命令，例如 `vim`。

`$JULIA_EDITOR` 优先于 `$VISUAL`，而 `$VISUAL` 又优先于 `$EDITOR`。如果这些环境变量都没有设置，则在 Windows 和 OS X 上，编辑器被视为 `open`，如果 `/etc/alternatives/editor` 存在，则使用它，否则使用 `emacs`。

要在 Windows 上使用 Visual Studio Code，请将 `$JULIA_EDITOR` 设置为 `code.cmd`。

## Parallelization

### [`JULIA_CPU_THREADS`](@id JULIA_CPU_THREADS)

覆盖全局变量 [`Base.Sys.CPU_THREADS`](@ref)，可用的逻辑 CPU 核心数量。

### [`JULIA_WORKER_TIMEOUT`](@id JULIA_WORKER_TIMEOUT)

一个 [`Float64`](@ref)，它设置了 `Distributed.worker_timeout()` 的值（默认值：`60.0`）。此函数给出了工作进程在死亡之前等待主进程建立连接的秒数。

### [`JULIA_NUM_THREADS`](@id JULIA_NUM_THREADS)

一个无符号的64位整数（`uint64_t`），用于设置可用于Julia的最大线程数。如果`$JULIA_NUM_THREADS`不是正数或未设置，或者无法通过系统调用确定CPU线程的数量，则线程数设置为`1`。

如果 `$JULIA_NUM_THREADS` 被设置为 `auto`，那么线程数将被设置为 CPU 线程的数量。

!!! note
    `JULIA_NUM_THREADS` 必须在启动 julia 之前定义；在 `startup.jl` 中定义则太晚了。


!!! compat "Julia 1.5"
    在 Julia 1.5 及以上版本中，线程的数量也可以在启动时通过 `-t`/`--threads` 命令行参数指定。


!!! compat "Julia 1.7"
    `$JULIA_NUM_THREADS` 的 `auto` 值需要 Julia 1.7 或更高版本。


### [`JULIA_THREAD_SLEEP_THRESHOLD`](@id JULIA_THREAD_SLEEP_THRESHOLD)

如果设置为以不区分大小写的子字符串 `"infinite"` 开头的字符串，则旋转线程将永不休眠。否则，`$JULIA_THREAD_SLEEP_THRESHOLD` 被解释为无符号 64 位整数（`uint64_t`），并以纳秒为单位给出旋转线程应休眠的时间。

### [`JULIA_NUM_GC_THREADS`](@id JULIA_NUM_GC_THREADS)

设置垃圾收集使用的线程数。如果未指定，则设置为工作线程数的一半。

!!! compat "Julia 1.10"
    环境变量是在1.10中添加的


### [`JULIA_IMAGE_THREADS`](@id JULIA_IMAGE_THREADS)

一个无符号的32位整数，用于设置此Julia进程中图像编译使用的线程数。如果模块是一个小模块，则可能会忽略此变量的值。如果未指定，则使用[`JULIA_CPU_THREADS`](@ref JULIA_CPU_THREADS)的值或逻辑CPU核心数量的一半中的较小者。

### [`JULIA_IMAGE_TIMINGS`](@id JULIA_IMAGE_TIMINGS)

一个布尔值，用于确定在图像编译期间是否打印详细的时间信息。默认为0。

### [`JULIA_EXCLUSIVE`](@id JULIA_EXCLUSIVE)

如果设置为除 `0` 以外的任何值，则 Julia 的线程策略与在专用机器上运行一致：主线程在处理器 0 上，线程是绑定的。否则，Julia 让操作系统处理线程策略。

## REPL formatting

环境变量决定了 REPL 输出在终端的格式。通常，这些变量应该设置为 [ANSI terminal escape sequences](https://en.wikipedia.org/wiki/ANSI_escape_code)。Julia 提供了一个高级接口，具有许多相同的功能；请参阅关于 [The Julia REPL](@ref) 的部分。

### [`JULIA_ERROR_COLOR`](@id JULIA_ERROR_COLOR)

格式 `Base.error_color()`（默认：浅红色，`"\033[91m"`）用于终端中显示错误。

### [`JULIA_WARN_COLOR`](@id JULIA_WARN_COLOR)

格式 `Base.warn_color()`（默认：黄色，`"\033[93m"`）用于终端中的警告。

### [`JULIA_INFO_COLOR`](@id JULIA_INFO_COLOR)

格式 `Base.info_color()`（默认：青色，`"\033[36m"`）应在终端中显示的信息。

### [`JULIA_INPUT_COLOR`](@id JULIA_INPUT_COLOR)

格式 `Base.input_color()`（默认值：normal，`"\033[0m"`）应在终端中具有的输入。

### [`JULIA_ANSWER_COLOR`](@id JULIA_ANSWER_COLOR)

格式 `Base.answer_color()`（默认值：正常，`"\033[0m"`）应在终端输出。

## System and Package Image Building

### [`JULIA_CPU_TARGET`](@id JULIA_CPU_TARGET)

修改目标机器架构以（预）编译 [system](@ref sysimg-multi-versioning) 和 [package images](@ref pkgimgs-multi-versioning)。`JULIA_CPU_TARGET` 仅影响输出到磁盘缓存的机器代码映像生成。与 `--cpu-target` 或 `-C` 不同，[command line option](@ref cli) 不影响 Julia 会话中的即时编译（JIT）代码生成，在该会话中，机器代码仅存储在内存中。

有效值可以通过执行 `julia -C help` 获得 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET)。

设置 [`JULIA_CPU_TARGET`](@ref JULIA_CPU_TARGET) 对于异构计算系统非常重要，因为可能存在不同类型或特征的处理器。这在高性能计算（HPC）集群中很常见，因为组件节点可能使用不同的处理器。

CPU目标字符串是一个由 `;` 分隔的字符串列表，每个字符串以CPU或架构名称开头，后面跟着一个可选的特性列表，特性之间用 `,` 分隔。一个 `generic` 或空的CPU名称意味着目标ISA的基本所需特性集，至少是C/C++运行时编译时所使用的架构。每个字符串由LLVM解释。

支持一些特殊功能：

1. `克隆所有`

    这迫使目标克隆 sysimg 中的所有函数。当以负形式使用时（即 `-clone_all`），这会禁用默认情况下为某些目标启用的完整克隆。
2. `base([0-9]*)`

    这指定了（0 基础）基础目标索引。基础目标是当前目标所基于的目标，即未被克隆的函数将使用基础目标中的版本。如果基础目标不是默认目标（0），则此选项会导致基础目标被完全克隆（就像为其指定了 `clone_all` 一样）。索引只能小于当前索引。
3. `opt_size`

    优化大小，最小化性能影响。Clang/GCC 的 `-Os`。
4. `最小大小`

    优化仅针对大小。Clang 的 `-Oz`。

## Debugging and profiling

### [`JULIA_DEBUG`](@id JULIA_DEBUG)

启用文件或模块的调试日志记录，请参见 [`Logging`](@ref man-logging) 以获取更多信息。

### [`JULIA_PROFILE_PEEK_HEAP_SNAPSHOT`](@id JULIA_PROFILE_PEEK_HEAP_SNAPSHOT)

在执行期间通过分析快照机制启用堆快照的收集。请参见 [Triggered During Execution](@ref)。

### [`JULIA_TIMING_SUBSYSTEMS`](@id JULIA_TIMING_SUBSYSTEMS)

允许您为特定的 Julia 运行启用或禁用区域。例如，将变量设置为 `+GC,-INFERENCE` 将启用 `GC` 区域并禁用 `INFERENCE` 区域。请参见 [Dynamically Enabling and Disabling Zones](@ref)。

### [`JULIA_GC_ALLOC_POOL`](@id JULIA_GC_ALLOC_POOL)

### [`JULIA_GC_ALLOC_OTHER`](@id JULIA_GC_ALLOC_OTHER)

### [`JULIA_GC_ALLOC_PRINT`](@id JULIA_GC_ALLOC_PRINT)

如果设置了这些环境变量，它们接受的字符串可以选择性地以字符 `'r'` 开头，后面跟着一个由冒号分隔的三个有符号 64 位整数（`int64_t`）的字符串插值。这个整数三元组 `a:b:c` 表示算术序列 `a`、`a + b`、`a + 2*b`，... `c`。

  * 如果这是 `jl_gc_pool_alloc()` 被调用的第 `n` 次，并且 `n` 属于由 `$JULIA_GC_ALLOC_POOL` 表示的算术序列，则强制进行垃圾回收。
  * 如果这是 `maybe_collect()` 被调用的第 `n` 次，并且 `n` 属于由 `$JULIA_GC_ALLOC_OTHER` 表示的算术序列，则强制进行垃圾收集。
  * 如果这是第 `n` 次调用 `jl_gc_collect()`，并且 `n` 属于由 `$JULIA_GC_ALLOC_PRINT` 表示的算术序列，则会打印对 `jl_gc_pool_alloc()` 和 `maybe_collect()` 的调用次数。

如果环境变量的值以字符 `'r'` 开头，则垃圾收集事件之间的间隔将是随机的。

!!! note
    这些环境变量仅在 Julia 以垃圾收集调试编译时才有效（即，如果在构建配置中将 `WITH_GC_DEBUG_ENV` 设置为 `1`）。


### [`JULIA_GC_NO_GENERATIONAL`](@id JULIA_GC_NO_GENERATIONAL)

如果设置为除 `0` 以外的任何值，则 Julia 垃圾收集器将永远不会执行内存的“快速清扫”。

!!! note
    此环境变量仅在 Julia 使用垃圾回收调试编译时有效（即，如果在构建配置中将 `WITH_GC_DEBUG_ENV` 设置为 `1`）。


### [`JULIA_GC_WAIT_FOR_DEBUGGER`](@id JULIA_GC_WAIT_FOR_DEBUGGER)

如果设置为除 `0` 以外的任何值，则 Julia 垃圾收集器将在发生严重错误时等待调试器附加，而不是中止。

!!! note
    此环境变量仅在 Julia 使用垃圾回收调试编译时有效（即，如果在构建配置中将 `WITH_GC_DEBUG_ENV` 设置为 `1`）。


### [`ENABLE_JITPROFILING`](@id ENABLE_JITPROFILING)

如果设置为除 `0` 以外的任何值，则编译器将创建并注册一个用于即时（JIT）分析的事件监听器。

!!! note
    此环境变量仅在 Julia 使用 JIT 性能分析支持编译时有效，使用任一

      * 英特尔的 [VTune™ Amplifier](https://software.intel.com/en-us/vtune) （在构建配置中将 `USE_INTEL_JITEVENTS` 设置为 `1`），或者
      * [OProfile](https://oprofile.sourceforge.io/news/)（在构建配置中将 `USE_OPROFILE_JITEVENTS` 设置为 `1`）。
      * [Perf](https://perf.wiki.kernel.org)（在构建配置中将 `USE_PERF_JITEVENTS` 设置为 `1`）。此集成默认启用。


### [`ENABLE_GDBLISTENER`](@id ENABLE_GDBLISTENER)

如果设置为除 `0` 以外的任何值，则在发布构建中启用 GDB 注册 Julia 代码。在 Julia 的调试构建中，这始终是启用的。建议与 `-g 2` 一起使用。

### [`JULIA_LLVM_ARGS`](@id JULIA_LLVM_ARGS)

传递给LLVM后端的参数。

### `JULIA_FALLBACK_REPL`

强制使用后备 REPL，而不是 REPL.jl。
