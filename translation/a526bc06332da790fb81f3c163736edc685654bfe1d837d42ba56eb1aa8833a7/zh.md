```
Base.touch(::Pidfile.LockMonitor)
```

更新锁的 `mtime`，以表明它仍然是新鲜的。

另请参见 [`mkpidlock`](@ref) 构造函数中的 `refresh` 关键字。
