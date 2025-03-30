```
put!(rr::Future, v)
```

将一个值存储到一个 [`Future`](@ref) `rr`。`Future` 是一次性写入的远程引用。对已经设置的 `Future` 进行 `put!` 会抛出一个 `Exception`。所有异步远程调用返回 `Future`，并在完成时将值设置为调用的返回值。
