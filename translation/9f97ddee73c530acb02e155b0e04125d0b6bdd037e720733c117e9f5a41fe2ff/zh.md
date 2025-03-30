```
trylock(lock) -> Success (Boolean)
```

如果锁可用，则获取锁，并在成功时返回 `true`。如果锁已被其他任务/线程锁定，则返回 `false`。

每个成功的 `trylock` 必须与 [`unlock`](@ref) 匹配。

函数 `trylock` 结合 [`islocked`](@ref) 可用于编写测试-测试-设置或指数退避算法 *如果 `typeof(lock)` 支持此功能*（请阅读其文档）。
