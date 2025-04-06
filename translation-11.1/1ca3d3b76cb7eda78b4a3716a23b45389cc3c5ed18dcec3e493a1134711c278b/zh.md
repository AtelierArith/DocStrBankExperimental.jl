# [Command-line Interface](@id cli)

## Using arguments inside scripts

在使用 `julia` 运行脚本时，可以向脚本传递额外的参数：

```
$ julia script.jl arg1 arg2...
```

这些额外的命令行参数通过全局常量 `ARGS` 传递。脚本本身的名称作为全局 `PROGRAM_FILE` 传递。请注意，当在命令行上使用 `-e` 选项给出 Julia 表达式时，`ARGS` 也会被设置（请参见下面的 `julia` 帮助输出），但 `PROGRAM_FILE` 将为空。例如，要仅仅打印传递给脚本的参数，你可以这样做：

```
$ julia -e 'println(PROGRAM_FILE); for x in ARGS; println(x); end' foo bar

foo
bar
```

或者你可以把那段代码放入一个脚本中并运行它：

```
$ echo 'println(PROGRAM_FILE); for x in ARGS; println(x); end' > script.jl
$ julia script.jl foo bar
script.jl
foo
bar
```

`--` 分隔符可用于将针对脚本文件的命令行参数与针对 Julia 的参数分开：

```
$ julia --color=yes -O -- script.jl arg1 arg2..
```

另请参阅 [Scripting](@ref man-scripting) 以获取有关编写 Julia 脚本的更多信息。

## The `Main.main` entry point

截至 Julia 1.11，`Base` 导出了宏 `@main`。该宏扩展为符号 `main`，但在执行脚本或表达式结束时，如果定义了这样的函数，并且通过使用 `@main` 宏选择了这种行为，`julia` 将尝试执行函数 `Main.main(ARGS)`。

此功能旨在帮助统一编译和交互式工作流。在编译工作流中，加载定义 `main` 函数的代码可能在空间和时间上与调用分开。然而，对于交互式工作流，其行为等同于在评估的脚本或表达式结束时显式调用 `exit(main(ARGS))`。

!!! compat "Julia 1.11"
    特殊入口点 `Main.main` 在 Julia 1.11 中添加。为了与之前的 Julia 版本兼容，请在脚本末尾添加显式的 `@isdefined(var"@main") ? (@main) : exit(main(ARGS))`。


要查看此功能的实际效果，请考虑以下定义，尽管没有对 `main` 的显式调用，但仍会执行打印函数：

```
$ julia -e '(@main)(args) = println("Hello World!")'
Hello World!
$
```

只有在定义模块中使用了宏 `@main` 时，`Main` 模块中的 `main` 绑定才具有这种行为。

例如，使用 `hello` 而不是 `main` 将不会导致 `hello` 函数执行：

```
$ julia -e 'hello(ARGS) = println("Hello World!")'
$
```

并且一个简单的 `main` 定义也不会：

```
$ julia -e 'main(ARGS) = println("Hello World!")'
$
```

然而，选择加入不必在定义时发生：

```
$ julia -e 'main(ARGS) = println("Hello World!"); @main'
Hello World!
$
```

`main` 绑定可以从一个包中导入。一个定义为 *hello world* 的包

```
module Hello

export main
(@main)(args) = println("Hello from the package!")

end
```

可能用作：

```
$ julia -e 'using Hello'
Hello from the package!
$ julia -e 'import Hello' # N.B.: Execution depends on the binding not whether the package is loaded
$
```

然而，请注意，目前的最佳实践建议是不要将应用程序代码和可重用库代码混合在同一个包中。辅助应用程序可以作为单独的包分发，或作为具有单独 `main` 入口点的脚本放在包的 `bin` 文件夹中。

## Parallel mode

Julia 可以通过 `-p` 或 `--machine-file` 选项以并行模式启动。`-p n` 将启动额外的 `n` 个工作进程，而 `--machine-file file` 将为文件 `file` 中的每一行启动一个工作进程。文件中定义的机器必须能够通过无密码的 `ssh` 登录访问，并且在与当前主机相同的位置安装了 Julia。每个机器定义的格式为 `[count*][user@]host[:port] [bind_addr[:port]]`。`user` 默认为当前用户，`port` 默认为标准 ssh 端口。`count` 是要在节点上生成的工作进程数量，默认为 1。可选的 `bind-to bind_addr[:port]` 指定其他工作进程应使用的连接到此工作进程的 IP 地址和端口。

## Startup file

如果您有希望在每次运行 Julia 时执行的代码，可以将其放入 `~/.julia/config/startup.jl`：

```
$ echo 'println("Greetings! 你好! 안녕하세요?")' > ~/.julia/config/startup.jl
$ julia
Greetings! 你好! 안녕하세요?

...
```

请注意，尽管在您第一次运行 Julia 后应该会有一个 `~/.julia` 目录，但如果您使用它，您可能需要创建 `~/.julia/config` 文件夹和 `~/.julia/config/startup.jl` 文件。

要使启动代码仅在 [The Julia REPL](@ref) 中运行（而不是在例如运行脚本时的 `julia`），请在 `startup.jl` 中使用 [`atreplinit`](@ref)：

```julia
atreplinit() do repl
    # ...
end
```

## [Command-line switches for Julia](@id command-line-interface)

有多种方法可以运行 Julia 代码，并提供选项，类似于 `perl` 和 `ruby` 程序可用的选项：

```
julia [switches] -- [programfile] [args...]
```

以下是启动 julia 时可用的命令行开关的完整列表（如果适用，'*' 标记默认值；标记为 '($)' 的设置可能会触发包的预编译）：

| Switch                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------------------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-v`, `--version`                                 | Display version information                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-h`, `--help`                                    | Print command-line options (this message)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `--help-hidden`                                   | Print uncommon options not shown by `-h`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `--project[={<dir>\|@.}]`                         | Set `<dir>` as the active project/environment. The default `@.` option will search through parent directories until a `Project.toml` or `JuliaProject.toml` file is found.                                                                                                                                                                                                                                                                                                                                                                                    |
| `-J`, `--sysimage <file>`                         | Start up with the given system image file                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-H`, `--home <dir>`                              | Set location of `julia` executable                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `--startup-file={yes*\|no}`                       | Load `JULIA_DEPOT_PATH/config/startup.jl`; if [`JULIA_DEPOT_PATH`](@ref JULIA_DEPOT_PATH) environment variable is unset, load `~/.julia/config/startup.jl`                                                                                                                                                                                                                                                                                                                                                                                                    |
| `--handle-signals={yes*\|no}`                     | Enable or disable Julia's default signal handlers                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `--sysimage-native-code={yes*\|no}`               | Use native code from system image if available                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `--compiled-modules={yes*\|no\|existing\|strict}` | Enable or disable incremental precompilation of modules. The `existing` option allows use of existing compiled modules that were previously precompiled, but disallows creation of new precompile files. The `strict` option is similar, but will error if no precompile file is found.                                                                                                                                                                                                                                                                       |
| `--pkgimages={yes*\|no\|existing}`                | Enable or disable usage of native code caching in the form of pkgimages. The `existing` option allows use of existing pkgimages but disallows creation of new ones                                                                                                                                                                                                                                                                                                                                                                                            |
| `-e`, `--eval <expr>`                             | Evaluate `<expr>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-E`, `--print <expr>`                            | Evaluate `<expr>` and display the result                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-m`, `--module <Package> [args]`                 | Run entry point of `Package` (`@main` function) with `args'                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-L`, `--load <file>`                             | Load `<file>` immediately on all processors                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-t`, `--threads {auto\|N[,auto\|M]}`             | Enable N[+M] threads; N threads are assigned to the `default` threadpool, and if M is specified, M threads are assigned to the `interactive` threadpool; `auto` tries to infer a useful default number of threads to use but the exact behavior might change in the future. Currently sets N to the number of CPUs assigned to this Julia process based on the OS-specific affinity assignment interface if supported (Linux and Windows) or to the number of CPU threads if not supported (MacOS) or if process affinity is not configured, and sets M to 1. |
| `--gcthreads=N[,M]`                               | Use N threads for the mark phase of GC and M (0 or 1) threads for the concurrent sweeping phase of GC. N is set to half of the number of compute threads and M is set to 0 if unspecified.                                                                                                                                                                                                                                                                                                                                                                    |
| `-p`, `--procs {N\|auto}`                         | Integer value N launches N additional local worker processes; `auto` launches as many workers as the number of local CPU threads (logical cores)                                                                                                                                                                                                                                                                                                                                                                                                              |
| `--machine-file <file>`                           | Run processes on hosts listed in `<file>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-i`, `--interactive`                             | Interactive mode; REPL runs and `isinteractive()` is true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-q`, `--quiet`                                   | Quiet startup: no banner, suppress REPL warnings                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `--banner={yes\|no\|short\|auto*}`                | Enable or disable startup banner                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `--color={yes\|no\|auto*}`                        | Enable or disable color text                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `--history-file={yes*\|no}`                       | Load or save history                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `--depwarn={yes\|no*\|error}`                     | Enable or disable syntax and method deprecation warnings (`error` turns warnings into errors)                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `--warn-overwrite={yes\|no*}`                     | Enable or disable method overwrite warnings                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `--warn-scope={yes*\|no}`                         | Enable or disable warning for ambiguous top-level scope                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-C`, `--cpu-target <target>`                     | Limit usage of CPU features up to `<target>`; set to `help` to see the available options                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-O`, `--optimize={0\|1\|2*\|3}`                  | Set the optimization level (level is 3 if `-O` is used without a level) ($)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `--min-optlevel={0*\|1\|2\|3}`                    | Set the lower bound on per-module optimization                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-g`, `--debug-info={0\|1*\|2}`                   | Set the level of debug info generation (level is 2 if `-g` is used without a level) ($)                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `--inline={yes\|no}`                              | Control whether inlining is permitted, including overriding `@inline` declarations                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `--check-bounds={yes\|no\|auto*}`                 | Emit bounds checks always, never, or respect `@inbounds` declarations ($)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `--math-mode={ieee,fast}`                         | Disallow or enable unsafe floating point optimizations (overrides `@fastmath` declaration)                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `--polly={yes*\|no}`                              | Enable or disable the polyhedral optimizer Polly (overrides @polly declaration)                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `--code-coverage[={none*\|user\|all}]`            | Count executions of source lines (omitting setting is equivalent to `user`)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `--code-coverage=@<path>`                         | Count executions but only in files that fall under the given file path/directory. The `@` prefix is required to select this option. A `@` with no path will track the current directory.                                                                                                                                                                                                                                                                                                                                                                      |
| `--code-coverage=tracefile.info`                  | Append coverage information to the LCOV tracefile (filename supports format tokens).                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `--track-allocation[={none*\|user\|all}]`         | Count bytes allocated by each source line (omitting setting is equivalent to "user")                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `--track-allocation=@<path>`                      | Count bytes but only in files that fall under the given file path/directory. The `@` prefix is required to select this option. A `@` with no path will track the current directory.                                                                                                                                                                                                                                                                                                                                                                           |
| `--bug-report=KIND`                               | Launch a bug report session. It can be used to start a REPL, run a script, or evaluate expressions. It first tries to use BugReporting.jl installed in current environment and falls back to the latest compatible BugReporting.jl if not. For more information, see `--bug-report=help`.                                                                                                                                                                                                                                                                     |
| `--heap-size-hint=<size>`                         | Forces garbage collection if memory usage is higher than the given value. The value may be specified as a number of bytes, optionally in units of KB, MB, GB, or TB, or as a percentage of physical memory with %.                                                                                                                                                                                                                                                                                                                                            |
| `--compile={yes*\|no\|all\|min}`                  | Enable or disable JIT compiler, or request exhaustive or minimal compilation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `--output-o <name>`                               | Generate an object file (including system image data)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `--output-ji <name>`                              | Generate a system image data file (.ji)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `--strip-metadata`                                | Remove docstrings and source location info from system image                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `--strip-ir`                                      | Remove IR (intermediate representation) of compiled functions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `--output-unopt-bc <name>`                        | Generate unoptimized LLVM bitcode (.bc)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `--output-bc <name>`                              | Generate LLVM bitcode (.bc)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `--output-asm <name>`                             | Generate an assembly file (.s)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `--output-incremental={yes\|no*}`                 | Generate an incremental output file (rather than complete)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `--trace-compile={stderr\|name}`                  | Print precompile statements for methods compiled during execution or save to a path                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `--image-codegen`                                 | Force generate code in imaging mode                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `--permalloc-pkgimg={yes\|no*}`                   | Copy the data section of package images into memory                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

!!! compat "Julia 1.1"
    在 Julia 1.0 中，默认的 `--project=@.` 选项不会从 Git 仓库的根目录向上搜索 `Project.toml` 文件。从 Julia 1.1 开始，它会这样做。

