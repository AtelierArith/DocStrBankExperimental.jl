```
open(filename::AbstractString; lock = true, keywords...) -> IOStream
```

以五个布尔关键字参数指定的模式打开文件：

| 关键字        | 描述       | 默认                                    |
|:---------- |:-------- |:------------------------------------- |
| `read`     | 以读取模式打开  | `!write`                              |
| `write`    | 以写入模式打开  | `truncate \| append`                  |
| `create`   | 如果不存在则创建 | `!read & write \| truncate \| append` |
| `truncate` | 截断为零大小   | `!read & write`                       |
| `append`   | 定位到文件末尾  | `false`                               |

当没有传递关键字时，默认以只读模式打开文件。返回一个用于访问打开文件的流。

`lock`关键字参数控制操作是否会被锁定以确保安全的多线程访问。

!!! compat "Julia 1.5"
    从Julia 1.5开始，`lock`参数可用。

