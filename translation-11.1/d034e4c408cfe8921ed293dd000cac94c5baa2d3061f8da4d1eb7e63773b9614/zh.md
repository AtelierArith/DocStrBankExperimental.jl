```
watch_file(path::AbstractString, timeout_s::Real=-1)
```

监视文件或目录 `path` 的更改，直到发生更改或经过 `timeout_s` 秒。此函数不轮询文件系统，而是使用特定于平台的功能从操作系统接收通知（例如，在 Linux 上通过 inotify）。有关详细信息，请参见下面链接的 NodeJS 文档。

返回的值是一个具有布尔字段 `renamed`、`changed` 和 `timedout` 的对象，给出监视文件的结果。

此函数的行为在不同平台之间略有不同。有关更详细的信息，请参见 [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats)。
