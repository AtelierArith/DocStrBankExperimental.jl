```
pushdisplay(d::AbstractDisplay)
```

将新的显示 `d` 推送到全局显示后端栈的顶部。调用 `display(x)` 或 `display(mime, x)` 将在栈中最上面的兼容后端上显示 `x`（即，最上面的不会抛出 [`MethodError`](@ref) 的后端）。
