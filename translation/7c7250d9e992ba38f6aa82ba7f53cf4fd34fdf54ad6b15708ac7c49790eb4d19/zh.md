```
open_exclusive(path::String; mode, poll_interval, wait, stale_age, refresh) :: File
```

创建一个新的文件以进行读写建议独占访问。如果 `wait` 为 `false`，则在锁文件存在时出错，否则阻塞直到我们获得锁。

有关关键字参数的描述，请参见 [`mkpidlock`](@ref)。
