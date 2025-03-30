```
open(command, mode::AbstractString, stdio=devnull)
```

异步运行 `command`。类似于 `open(command, stdio; read, write)`，但通过模式字符串而不是关键字参数来指定读取和写入标志。可能的模式字符串有：

| 模式   | 描述     | 关键字                         |
|:---- |:------ |:--------------------------- |
| `r`  | 读取     | 无                           |
| `w`  | 写入     | `write = true`              |
| `r+` | 读取, 写入 | `read = true, write = true` |
| `w+` | 读取, 写入 | `read = true, write = true` |
