```
with(f::Function, obj)
```

资源管理辅助函数。将 `f` 应用到 `obj`，确保在 `f` 成功返回或抛出错误后调用 `close` 以关闭 `obj`。确保分配的 git 资源在不再需要时尽快被释放。
