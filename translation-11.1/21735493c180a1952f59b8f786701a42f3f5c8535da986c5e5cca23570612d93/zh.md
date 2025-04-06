```
analyze_escapes(ir::IRCode, nargs::Int, get_escape_cache) -> estate::EscapeState
```

分析 `ir` 中的逃逸信息：

  * `nargs`: 被分析调用的实际参数数量
  * `get_escape_cache(::MethodInstance) -> Union{Bool,ArgEscapeCache}`: 检索缓存的参数逃逸信息
