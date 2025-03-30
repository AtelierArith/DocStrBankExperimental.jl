```
remove_frames!(stack::StackTrace, name::Symbol)
```

接受一个 `StackTrace`（一个 `StackFrames` 的向量）和一个函数名（一个 `Symbol`），并从 `StackTrace` 中移除由函数名指定的 `StackFrame`（同时移除指定函数之上的所有帧）。主要用于在返回之前从 `StackTrace` 中移除 `StackTraces` 函数。
