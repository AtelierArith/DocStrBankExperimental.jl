```
errno([code])
```

获取 C 库的 `errno` 值。如果指定了参数，则用于设置 `errno` 的值。

`errno` 的值仅在对设置它的 C 库例程的 `ccall` 之后立即有效。具体来说，您不能在 REPL 的下一个提示符中调用 `errno`，因为在提示符之间执行了大量代码。
