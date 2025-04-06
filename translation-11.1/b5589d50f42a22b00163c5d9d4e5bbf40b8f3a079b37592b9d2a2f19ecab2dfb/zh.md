```
dlsym(handle, sym; throw_error::Bool = true)
```

从共享库句柄中查找符号，成功时返回可调用的函数指针。

如果找不到符号，此方法会抛出错误，除非关键字参数 `throw_error` 被设置为 `false`，在这种情况下，此方法返回 `nothing`。
