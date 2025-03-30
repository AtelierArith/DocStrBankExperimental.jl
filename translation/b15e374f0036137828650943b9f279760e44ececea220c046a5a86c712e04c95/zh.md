# Reporting and analyzing crashes (segfaults)

所以你成功地破坏了 Julia。恭喜你！这里收集了一些常见症状的通用处理程序，当出现问题时可以进行这些处理。包括这些调试步骤的信息可以大大帮助维护者在追踪段错误或试图弄清楚为什么你的脚本运行得比预期慢时。

如果您被引导到此页面，请找到与您所经历的症状最匹配的症状，并按照说明生成所请求的调试信息。症状表：

  * [Segfaults during bootstrap (`sysimg.jl`)](@ref)
  * [Segfaults when running a script](@ref)
  * [Errors during Julia startup](@ref)
  * [Other generic segfaults or unreachables reached](@ref)

## [Version/Environment info](@id dev-version-info)

无论错误是什么，我们始终需要知道您正在运行的 Julia 版本。当 Julia 首次启动时，会打印出带有版本号和日期的标题。请在您创建的任何报告中也包含 `versioninfo()` 的输出（从 [`InteractiveUtils`](@ref InteractiveUtils.versioninfo) 标准库导出）：

```@repl
using InteractiveUtils
versioninfo()
```

## Segfaults during bootstrap (`sysimg.jl`)

在构建 Julia 的 `make` 过程接近尾声时出现段错误是一个常见的症状，通常表明在 Julia 预解析 `base/` 文件夹中的代码时出现了问题。许多因素可能导致这个过程意外终止，但这往往是由于 Julia 的 C 代码部分中的错误，因此通常需要在 `gdb` 中使用调试构建进行调试。明确地说：

创建 Julia 的调试构建：

```
$ cd <julia_root>
$ make debug
```

请注意，此过程可能会以与正常 `make` 命令相同的错误失败，但这将创建一个调试可执行文件，为 `gdb` 提供获取准确回溯所需的调试符号。接下来，在 `gdb` 中手动运行引导过程：

```
$ cd base/
$ gdb -x ../contrib/debug_bootstrap.gdb
```

这将启动 `gdb`，尝试使用 Julia 的调试构建运行引导过程，并在发生段错误时打印出回溯。您可能需要按几次 `<enter>` 以获取完整的回溯。创建一个 [gist](https://gist.github.com)，包含回溯、[version info](@ref dev-version-info) 以及您能想到的任何其他相关信息，并在 Github 上打开一个新的 [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen)，并附上指向 gist 的链接。

## Segfaults when running a script

该过程与 [Segfaults during bootstrap (`sysimg.jl`)](@ref) 非常相似。创建一个 Julia 的调试构建，并在调试的 Julia 进程中运行您的脚本：

```
$ cd <julia_root>
$ make debug
$ gdb --args usr/bin/julia-debug <path_to_your_script>
```

注意，`gdb` 将会在那儿等待指令。 输入 `r` 来运行进程，输入 `bt` 在发生段错误后生成回溯：

```
(gdb) r
Starting program: /home/sabae/src/julia/usr/bin/julia-debug ./test.jl
...
(gdb) bt
```

创建一个 [gist](https://gist.github.com)，附带回溯，[version info](@ref dev-version-info)，以及你能想到的任何其他相关信息，并在Github上打开一个新的 [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen)，并附上指向gist的链接。

## Errors during Julia startup

偶尔在Julia的启动过程中会发生错误（尤其是在使用二进制分发时，与从源代码编译相比），例如以下情况：

```julia
$ julia
exec: error -5
```

这些错误通常表明在启动阶段的早期，有些东西没有正确加载，我们确定问题所在的最佳方法是使用外部工具来审计 `julia` 进程的磁盘活动：

  * 在Linux上，使用`strace`：

    ```
    $ strace julia
    ```
  * 在OSX上，使用`dtruss`：

    ```
    $ dtruss -f julia
    ```

创建一个 [gist](https://gist.github.com)，包含 `strace`/ `dtruss` 输出，[version info](@ref dev-version-info)，以及任何其他相关信息，并在 Github 上打开一个新的 [issue](https://github.com/JuliaLang/julia/issues?q=is%3Aopen)，并附上指向 gist 的链接。

## Other generic segfaults or unreachables reached

如前所述，`julia` 与 `rr` 有良好的集成，用于生成跟踪；这包括在 Linux 上自动在 `rr` 下运行 `julia` 并在崩溃后共享跟踪的能力。这在调试此类崩溃时非常有帮助，并且在向 JuliaLang/julia 仓库报告崩溃问题时强烈建议使用。要自动在 `rr` 下运行 `julia`，请执行：

```julia
julia --bug-report=rr
```

要在本地生成 `rr` 跟踪，但不共享，可以执行：

```julia
julia --bug-report=rr-local
```

请注意，这仅适用于Linux。关于 [Time Travelling Bug Reporting](https://julialang.org/blog/2020/05/rr/) 的博客文章有更多详细信息。

## Glossary

在本指南中使用了一些术语作为简写：

  * `<julia_root>` 指的是 Julia 源代码树的根目录；例如，它应该包含 `base`、`deps`、`src`、`test` 等文件夹.....
