# [Getting Started](@id man-getting-started)

Julia 的安装非常简单，无论是使用预编译的二进制文件还是从源代码编译。通过按照 [https://julialang.org/downloads/](https://julialang.org/downloads/) 上的说明下载并安装 Julia。

如果您是从以下语言转向 Julia，那么您应该首先阅读关于与 [MATLAB](@ref Noteworthy-differences-from-MATLAB)、[R](@ref Noteworthy-differences-from-R)、[Python](@ref Noteworthy-differences-from-Python)、[C/C++](@ref Noteworthy-differences-from-C/C) 或 [Common Lisp](@ref Noteworthy-differences-from-Common-Lisp) 的显著差异的部分。这将帮助您避免一些常见的陷阱，因为 Julia 在许多微妙的方面与这些语言不同。

学习和实验Julia的最简单方法是通过双击Julia可执行文件或从命令行运行`julia`来启动一个交互式会话（也称为读取-评估-打印循环或“REPL”）：

```@eval
using REPL
io = IOBuffer()
REPL.banner(io)
banner = String(take!(io))
import Markdown
Markdown.parse("```\n\$ julia\n\n$(banner)\njulia> 1 + 2\n3\n\njulia> ans\n3\n```")
```

要退出交互式会话，请输入 `CTRL-D`（同时按下 Control/`^` 键和 `d` 键），或输入 `exit()`。在交互模式下运行时，`julia` 会显示一个横幅并提示用户输入。一旦用户输入了完整的表达式，例如 `1 + 2`，并按下回车，交互会话将评估该表达式并显示其值。如果在交互会话中输入的表达式以分号结尾，则其值不会显示。变量 `ans` 绑定到最后一个评估表达式的值，无论其是否显示。`ans` 变量仅在交互会话中绑定，而在以其他方式运行 Julia 代码时则不绑定。

要评估在源文件 `file.jl` 中编写的表达式，请写 `include("file.jl")`。

要以非交互方式运行文件中的代码，可以将其作为第一个参数传递给 `julia` 命令：

```
$ julia script.jl
```

您可以向 Julia 和您的程序 `script.jl` 传递额外的参数。所有可用选项的详细列表可以在 [Command-line Interface](@ref cli) 下找到。

## Resources

可以在主 Julia 网站的 [learning](https://julialang.org/learning/) 页面找到一份有用学习资源的策划列表，以帮助新用户入门。

您可以通过切换到帮助模式来使用 REPL 作为学习资源。在空的 `julia>` 提示符下按 `?` 切换到帮助模式，然后再输入其他内容。在帮助模式下输入关键字将获取该关键字的文档及示例。对于您可能遇到的大多数函数或其他对象也是如此！

```
help?> begin
search: begin disable_sigint reenable_sigint

  begin

  begin...end denotes a block of code.
```

如果你已经对 Julia 有一点了解，你可能想提前查看 [Performance Tips](@ref man-performance-tips) 和 [Workflow Tips](@ref man-workflow-tips)。
