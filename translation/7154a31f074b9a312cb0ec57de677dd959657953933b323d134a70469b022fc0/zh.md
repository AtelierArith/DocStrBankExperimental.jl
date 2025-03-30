```
poll_file(path::AbstractString, interval_s::Real=5.007, timeout_s::Real=-1) -> (previous::StatStruct, current)
```

通过每 `interval_s` 秒轮询一次来监视文件的变化，直到发生变化或 `timeout_s` 秒已过去。`interval_s` 应该是一个较长的时间段；默认值为 5.007 秒。

当检测到变化时，返回一对状态对象 `(previous, current)`。`previous` 状态始终是 `StatStruct`，但它的所有字段可能都为零（表示文件之前不存在或之前不可访问）。

`current` 状态对象可能是 `StatStruct`、`EOFError`（表示超时已过），或其他 `Exception` 子类型（如果 `stat` 操作失败 - 例如，如果路径不存在）。

要确定文件何时被修改，可以比较 `current isa StatStruct && mtime(prev) != mtime(current)` 来检测变化通知。然而，使用 [`watch_file`](@ref) 进行此操作更为优选，因为它更可靠且高效，尽管在某些情况下可能不可用。
