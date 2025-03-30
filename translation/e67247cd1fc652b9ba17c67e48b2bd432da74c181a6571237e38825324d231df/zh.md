```
handle_message(logger, level, message, _module, group, id, file, line; key1=val1, ...)
```

将消息记录到 `logger`，级别为 `level`。消息生成的逻辑位置由模块 `_module` 和 `group` 给出；源位置由 `file` 和 `line` 给出。`id` 是一个任意的唯一值（通常是一个 [`Symbol`](@ref)），用于在过滤时作为标识日志语句的键。
