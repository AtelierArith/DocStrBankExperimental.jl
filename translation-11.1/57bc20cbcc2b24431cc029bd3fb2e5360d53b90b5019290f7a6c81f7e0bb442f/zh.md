```
dlsym_e(handle, sym)
```

从共享库句柄中查找符号，在查找失败时静默返回 `C_NULL`。该方法现已弃用，建议使用 `dlsym(handle, sym; throw_error=false)`。
