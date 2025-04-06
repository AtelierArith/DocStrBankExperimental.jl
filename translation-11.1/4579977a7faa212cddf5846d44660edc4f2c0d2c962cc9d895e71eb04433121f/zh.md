```
mkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
mkpidlock(at::String, proc::Process; kwopts...)
```

为当前进程或由 pid 或 proc 标识的进程创建路径 "at" 的 pidfile 锁。可以传入一个函数，在锁定后执行，适用于 `do` 块，之后锁将自动关闭。如果锁定失败且 `wait` 为 false，则会抛出错误。

锁将通过 `close`、`finalizer` 或在 `proc` 退出后不久释放。确保返回值在程序的关键部分结束之前保持有效，以便 `finalizer` 不会过早回收它。

可选关键字参数：

  * `mode`: 文件访问模式（由进程 umask 修改）。默认为全局可读。
  * `poll_interval`: 指定尝试之间的最大时间（如果 `watch_file` 无效）
  * `stale_age`: 如果现有的 pidfile 的 mtime 超过此秒数，则删除该文件（忽略锁）。如果文件中的 pid 似乎有效，则文件不会在超过此时间的 5 倍后被删除。如果 `refresh` 被重写为 0 以禁用锁刷新，则为 25 倍。默认情况下此功能是禁用的（`stale_age` = 0），但典型的推荐值大约是估计正常完成时间的 3-5 倍。
  * `refresh`: 通过在每个经过的时间间隔更新 mtime 来防止锁变得陈旧。默认情况下，这设置为 `stale_age/2`，这是推荐值。
  * `wait`: 如果为 true，则阻塞直到获取锁；如果为 false，则在锁定失败时引发错误。
