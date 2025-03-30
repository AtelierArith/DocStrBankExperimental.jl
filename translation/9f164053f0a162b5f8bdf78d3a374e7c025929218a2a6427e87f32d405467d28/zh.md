# Using Valgrind with Julia

[Valgrind](https://valgrind.org/) 是一个用于内存调试、内存泄漏检测和性能分析的工具。本节描述了在使用 Valgrind 调试 Julia 的内存问题时需要注意的事项。

## General considerations

默认情况下，Valgrind 假设它运行的程序中没有自我修改的代码。这个假设在大多数情况下都能正常工作，但对于像 `julia` 这样的即时编译器来说却失败得很惨。因此，向 `valgrind` 传递 `--smc-check=all-non-file` 是至关重要的，否则代码可能会崩溃或表现出意外的行为（通常是微妙的方式）。

在某些情况下，为了更好地使用 Valgrind 检测内存错误，禁用内存池编译 `julia` 可能会有所帮助。编译时标志 `MEMDEBUG` 在 Julia 中禁用内存池，而 `MEMDEBUG2` 在 FemtoLisp 中禁用内存池。要使用这两个标志构建 `julia`，请将以下行添加到 `Make.user`：

```make
CFLAGS = -DMEMDEBUG -DMEMDEBUG2
```

另一个需要注意的事项是：如果您的程序使用多个工作进程，您可能希望所有这些工作进程都在 Valgrind 下运行，而不仅仅是父进程。要做到这一点，请将 `--trace-children=yes` 传递给 `valgrind`。

另一个需要注意的事项是：如果使用 `valgrind` 时出现 `Unable to find compatible target in system image` 错误，请尝试使用目标 `generic` 重新构建 sysimage 或使用 `JULIA_CPU_TARGET=generic` 重新构建 julia。

## Suppressions

Valgrind 通常会在运行时显示虚假警告。为了减少此类警告的数量，向 Valgrind 提供一个 [suppressions file](https://valgrind.org/docs/manual/manual-core.html#manual-core.suppress) 是有帮助的。一个示例抑制文件包含在 Julia 源代码分发中的 `contrib/valgrind-julia.supp`。

抑制文件可以从 `julia/` 源目录使用，如下所示：

```
$ valgrind --smc-check=all-non-file --suppressions=contrib/valgrind-julia.supp ./julia progname.jl
```

任何显示的内存错误应被报告为错误或作为额外的抑制进行贡献。请注意，某些版本的 Valgrind 是 [shipped with insufficient default suppressions](https://github.com/JuliaLang/julia/issues/8314#issuecomment-55766210)，因此在提交任何错误之前，这可能是需要考虑的一件事。

## Running the Julia test suite under Valgrind

可以在 Valgrind 下运行整个 Julia 测试套件，但确实需要相当长的时间（通常几个小时）。要做到这一点，请从 `julia/test/` 目录运行以下命令：

```
valgrind --smc-check=all-non-file --trace-children=yes --suppressions=$PWD/../contrib/valgrind-julia.supp ../julia runtests.jl all
```

如果您想查看“明确”的内存泄漏报告，请将标志 `--leak-check=full --show-leak-kinds=definite` 传递给 `valgrind`。

## Additional spurious warnings

本节涵盖了无法添加到抑制文件中的 Valgrind 警告，但这些警告仍然可以安全忽略。

### Unhandled rr system calls

Valgrind 会发出警告，如果它遇到任何 [system calls that are specific to rr](https://github.com/rr-debugger/rr/blob/master/src/preload/rrcalls.h)，以及 [Record and Replay Framework](https://rr-project.org/)。特别是，当 julia 尝试检测它是否在 rr 下运行时，将显示关于未处理的 `1008` 系统调用的警告：

```
--xxxxxx-- WARNING: unhandled amd64-linux syscall: 1008
--xxxxxx-- You may be able to write your own handler.
--xxxxxx-- Read the file README_MISSING_SYSCALL_OR_IOCTL.
--xxxxxx-- Nevertheless we consider this a bug.  Please report
--xxxxxx-- it at http://valgrind.org/support/bug_reports.html.
```

此问题 [has been reported](https://bugs.kde.org/show_bug.cgi?id=446401) 已提交给 Valgrind 开发者，因为他们已提出请求。

## Caveats

Valgrind 当前 [does not support multiple rounding modes](https://bugs.kde.org/show_bug.cgi?id=136779)，因此在 Valgrind 下运行的调整舍入模式的代码将表现不同。

一般来说，如果在设置 `--smc-check=all-non-file` 后发现您的程序在 Valgrind 下运行时表现不同，您可以在进一步调查时将 `--tool=none` 传递给 `valgrind`。这将启用最小的 Valgrind 机制，但运行速度会比启用完整内存检查器时快得多。
