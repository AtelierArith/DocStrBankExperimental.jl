```
islocked(lock) -> 状态 (布尔值)
```

检查 `lock` 是否被任何任务/线程持有。此函数本身不应用于同步。然而，`islocked` 结合 [`trylock`](@ref) 可以用于编写测试-测试-设置或指数退避算法 *如果 `typeof(lock)` 支持的话*（请阅读其文档）。

# 扩展帮助

例如，如果 `lock` 的实现满足下面文档中记录的属性，可以实现指数退避，如下所示。

```julia
nspins = 0
while true
    while islocked(lock)
        GC.safepoint()
        nspins += 1
        nspins > LIMIT && error("超时")
    end
    trylock(lock) && break
    backoff()
end
```

## 实现

建议锁的实现定义 `islocked`，并在其文档字符串中注明以下属性。

  * `islocked(lock)` 是无数据竞争的。
  * 如果 `islocked(lock)` 返回 `false`，则在没有其他任务干扰的情况下，立即调用 `trylock(lock)` 必须成功（返回 `true`）。
