```
stacktrace([trace::Vector{Ptr{Cvoid}},] [c_funcs::Bool=false]) -> StackTrace
```

返回一个以 `StackFrame` 形式的堆栈跟踪向量。（默认情况下，stacktrace 不返回 C 函数，但可以启用此功能。）当不指定 trace 调用时，`stacktrace` 首先调用 `backtrace`。
