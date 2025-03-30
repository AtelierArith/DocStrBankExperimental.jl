```
pipeline(from, to, ...)
```

创建一个从数据源到目的地的管道。源和目的地可以是命令、I/O 流、字符串或其他 `pipeline` 调用的结果。至少一个参数必须是命令。字符串指的是文件名。当使用超过两个参数调用时，它们会从左到右链接在一起。例如，`pipeline(a,b,c)` 等价于 `pipeline(pipeline(a,b),c)`。这提供了一种更简洁的方式来指定多阶段管道。

**示例**：

```julia
run(pipeline(`ls`, `grep xyz`))
run(pipeline(`ls`, "out.txt"))
run(pipeline("out.txt", `grep xyz`))
```
