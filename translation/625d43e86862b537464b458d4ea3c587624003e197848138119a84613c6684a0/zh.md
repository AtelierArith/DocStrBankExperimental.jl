```
remove_frames!(stack::StackTrace, m::Module)
```

返回 `StackTrace`，其中所有来自提供的 `Module` 的 `StackFrame` 都被移除。
