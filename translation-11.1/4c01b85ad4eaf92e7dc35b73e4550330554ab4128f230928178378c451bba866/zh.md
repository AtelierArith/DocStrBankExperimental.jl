```
InterruptException()
```

该进程被终端中断（CTRL+C）停止。

请注意，在没有 `-i`（交互式）选项启动的 Julia 脚本中，默认情况下不会抛出 `InterruptException`。在脚本中调用 [`Base.exit_on_sigint(false)`](@ref Base.exit_on_sigint) 可以恢复 REPL 的行为。或者，可以使用以下命令启动 Julia 脚本：

```sh
julia -e "include(popfirst!(ARGS))" script.jl
```

以便在执行期间让 CTRL+C 抛出 `InterruptException`。
