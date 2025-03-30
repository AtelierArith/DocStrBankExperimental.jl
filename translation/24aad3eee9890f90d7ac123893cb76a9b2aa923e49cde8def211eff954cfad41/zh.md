```
arg_isdir(f::Function, arg::AbstractString) -> f(arg)
```

`arg_isdir` 函数接受 `arg`，该参数必须是现有目录的路径（否则会引发错误），并将该路径传递给 `f`，最终返回 `f(arg)` 的结果。这无疑是 `ArgTools` 提供的最不实用的工具，主要是为了与 `arg_mkdir` 保持对称，并提供一致的错误消息。
