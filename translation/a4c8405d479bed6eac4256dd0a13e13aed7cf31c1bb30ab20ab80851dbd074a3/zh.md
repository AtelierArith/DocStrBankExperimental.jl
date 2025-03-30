```
poll_fd(fd, timeout_s::Real=-1; readable=false, writable=false)
```

监视文件描述符 `fd` 的读或写可用性变化，超时时间由 `timeout_s` 秒给出。

关键字参数决定了应监视读和/或写状态；至少其中一个必须设置为 `true`。

返回的值是一个具有布尔字段 `readable`、`writable` 和 `timedout` 的对象，给出轮询的结果。
