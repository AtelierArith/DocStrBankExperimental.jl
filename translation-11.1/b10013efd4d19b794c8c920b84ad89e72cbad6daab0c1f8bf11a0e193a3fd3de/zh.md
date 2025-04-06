```
Cmd(cmd::Cmd; ignorestatus, detach, windows_verbatim, windows_hide, env, dir)
Cmd(exec::Vector{String})
```

构造一个新的 `Cmd` 对象，表示一个外部程序及其参数，来自 `cmd`，同时更改可选关键字参数的设置：

  * `ignorestatus::Bool`：如果为 `true`（默认为 `false`），则 `Cmd` 在返回代码非零时不会抛出错误。
  * `detach::Bool`：如果为 `true`（默认为 `false`），则 `Cmd` 将在一个新的进程组中运行，允许它超出 `julia` 进程的生命周期，并且不会将 Ctrl-C 传递给它。
  * `windows_verbatim::Bool`：如果为 `true`（默认为 `false`），则在 Windows 上，`Cmd` 将以不进行引号或转义参数的方式将命令行字符串发送给进程，即使参数包含空格。（在 Windows 上，参数作为单个“命令行”字符串发送给程序，程序负责将其解析为参数。默认情况下，空参数和包含空格或制表符的参数在命令行中用双引号 `"` 引起来，并且 `\` 或 `"` 前面有反斜杠。`windows_verbatim=true` 对于启动以非标准方式解析其命令行的程序非常有用。）对非 Windows 系统没有影响。
  * `windows_hide::Bool`：如果为 `true`（默认为 `false`），则在 Windows 上执行 `Cmd` 时不会显示新的控制台窗口。如果已经打开控制台或在非 Windows 系统上，则没有影响。
  * `env`：设置运行 `Cmd` 时使用的环境变量。`env` 可以是一个将字符串映射到字符串的字典，一个形式为 `"var=val"` 的字符串数组，或一对 `"var"=>val` 的数组或元组。为了修改（而不是替换）现有环境，使用 `copy(ENV)` 初始化 `env`，然后根据需要设置 `env["var"]=val`。要在 `Cmd` 对象中添加环境块而不替换所有元素，请使用 [`addenv()`](@ref)，它将返回一个具有更新环境的 `Cmd` 对象。
  * `dir::AbstractString`：指定命令的工作目录（而不是当前目录）。

对于未指定的任何关键字，将使用 `cmd` 的当前设置。

请注意，`Cmd(exec)` 构造函数不会创建 `exec` 的副本。对 `exec` 的任何后续更改将反映在 `Cmd` 对象中。

构造 `Cmd` 对象的最常见方法是使用命令字面量（反引号），例如：

```
`ls -l`
```

然后可以将其传递给 `Cmd` 构造函数以修改其设置，例如：

```
Cmd(`echo "Hello world"`, ignorestatus=true, detach=false)
```
