`Header` 类型是一个结构体，表示 tar 文件中单个记录的基本元数据，其定义如下：

```
struct Header
    path :: String # 相对于根的路径
    type :: Symbol # 类型指示符（见下文）
    mode :: UInt16 # 模式/权限（最好以八进制查看）
    size :: Int64  # 记录数据的字节大小
    link :: String # 符号链接的目标路径
end
```

类型用以下符号表示：`file`、`hardlink`、`symlink`、`chardev`、`blockdev`、`directory`、`fifo`，或者对于未知类型，使用类型标志字符作为符号。请注意，[`extract`](@ref) 拒绝提取类型为 `file`、`symlink` 和 `directory` 以外的记录；[`list`](@ref) 仅在 `strict=false` 的情况下列出其他类型的记录。

tar 格式包含有关记录的各种其他元数据，包括用户和组 ID、用户和组名称以及时间戳。`Tar` 包故意完全忽略这些。在创建 tar 文件时，这些字段始终设置为零/空。在读取 tar 文件时，除了验证每个头记录的头部校验和外，这些字段会被忽略。
