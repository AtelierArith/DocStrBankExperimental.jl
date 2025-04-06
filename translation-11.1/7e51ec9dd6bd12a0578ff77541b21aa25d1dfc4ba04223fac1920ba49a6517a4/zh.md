```
@arg_test arg1 arg2 ... body
```

`@arg_test` 宏用于将 `arg_readers` 和 `arg_writers` 提供的 `arg` 函数转换为实际的参数值。当你写 `@arg_test arg body` 时，它等价于 `arg(arg -> body)`。
