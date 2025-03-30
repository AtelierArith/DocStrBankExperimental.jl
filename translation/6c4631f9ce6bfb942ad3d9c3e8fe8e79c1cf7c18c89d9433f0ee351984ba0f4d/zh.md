```
pipeline(command; stdin, stdout, stderr, append=false)
```

将输入/输出重定向到给定的 `command`。关键字参数指定应重定向命令的哪个流。`append` 控制文件输出是否追加到文件。这是 2 个参数的 `pipeline` 函数的更一般版本。当 `from` 是命令时，`pipeline(from, to)` 等价于 `pipeline(from, stdout=to)`，当 `from` 是另一种数据源时，等价于 `pipeline(to, stdin=from)`。

**示例**：

```julia
run(pipeline(`dothings`, stdout="out.txt", stderr="errs.txt"))
run(pipeline(`update`, stdout="log.txt", append=true))
```
