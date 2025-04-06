```
lookup(pointer::Ptr{Cvoid}) -> Vector{StackFrame}
```

给定一个指向执行上下文的指针（通常由对 `backtrace` 的调用生成），查找堆栈帧上下文信息。返回一个数组，其中包含在该点内联的所有函数的帧信息，最内层的函数优先。
