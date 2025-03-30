```
redisplay(x)
redisplay(d::AbstractDisplay, x)
redisplay(mime, x)
redisplay(d::AbstractDisplay, mime, x)
```

默认情况下，`redisplay` 函数简单地调用 [`display`](@ref)。然而，一些显示后端可能会重写 `redisplay` 以修改现有的 `x` 的显示（如果有的话）。使用 `redisplay` 也是对后端的一个提示，表明 `x` 可能会被多次重新显示，后端可能会选择推迟显示，直到（例如）下一个交互提示。
