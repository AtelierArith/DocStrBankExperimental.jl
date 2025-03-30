```
arg_mkdir(f::Function, arg::AbstractString) -> arg
arg_mkdir(f::Function, arg::Nothing) -> mktempdir()
```

`arg_mkdir` 函数接受 `arg`，它必须是以下之一：

  * 一个已存在的空目录的路径，
  * 一个可以创建为目录的不存在的路径，或者
  * `nothing`，在这种情况下会创建一个临时目录。

在所有情况下，返回目录的路径。如果在 `f(arg)` 执行期间发生错误，目录将恢复到其原始状态：如果它已经存在但为空，它将被清空；如果它不存在，它将被删除。
