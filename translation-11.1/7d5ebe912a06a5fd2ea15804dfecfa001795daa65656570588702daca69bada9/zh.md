```
__precompile__(isprecompilable::Bool)
```

指定调用此函数的文件是否可预编译，默认为 `true`。如果模块或文件*不*安全地可预编译，则应调用 `__precompile__(false)` 以便在 Julia 尝试预编译时抛出错误。
