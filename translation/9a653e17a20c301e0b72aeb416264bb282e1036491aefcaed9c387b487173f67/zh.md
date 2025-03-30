```
@static
```

在解析时部分求值一个表达式。

例如，`@static Sys.iswindows() ? foo : bar` 将会求值 `Sys.iswindows()` 并将 `foo` 或 `bar` 插入到表达式中。这在某些情况下非常有用，例如在其他平台上无效的构造，比如对不存在的函数的 `ccall`。`@static if Sys.isapple() foo end` 和 `@static foo <&&,||> bar` 也是有效的语法。
