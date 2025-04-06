```
@threadcall((cfunc, clib), rettype, (argtypes...), argvals...)
```

`@threadcall` 宏的调用方式与 [`ccall`](@ref) 相同，但在不同的线程中执行。这在您想要调用一个阻塞的 C 函数而不导致当前 `julia` 线程被阻塞时非常有用。并发性受到 libuv 线程池大小的限制，默认情况下为 4 个线程，但可以通过设置 `UV_THREADPOOL_SIZE` 环境变量并重新启动 `julia` 进程来增加。

请注意，被调用的函数绝不应回调到 Julia。
