```
exit_on_sigint(on::Bool)
```

设置 julia 运行时的 `exit_on_sigint` 标志。如果为 `false`，则 Ctrl-C (SIGINT) 可以在 `try` 块中捕获为 [`InterruptException`](@ref)。这是 REPL 中的默认行为，通过 `-e` 和 `-E` 运行的任何代码，以及使用 `-i` 选项运行的 Julia 脚本。

如果为 `true`，则 Ctrl-C 不会抛出 `InterruptException`。在此事件发生时运行代码需要 [`atexit`](@ref)。这是在没有 `-i` 选项运行的 Julia 脚本中的默认行为。

!!! compat "Julia 1.5"
    函数 `exit_on_sigint` 至少需要 Julia 1.5。

