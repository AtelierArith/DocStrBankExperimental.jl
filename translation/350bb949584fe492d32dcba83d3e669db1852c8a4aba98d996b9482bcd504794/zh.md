```
watch_folder(path::AbstractString, timeout_s::Real=-1)
```

监视文件或目录 `path` 的更改，直到发生更改或经过 `timeout_s` 秒。此函数不轮询文件系统，而是使用特定于平台的功能从操作系统接收通知（例如，在 Linux 上通过 inotify）。有关详细信息，请参阅下面链接的 NodeJS 文档。

在调用同一 `path` 的 `unwatch_folder` 之前，将在后台继续跟踪 `path` 的更改。

返回值是一个对，其中第一个字段是更改文件的名称（如果可用），第二个字段是一个对象，具有布尔字段 `renamed`、`changed` 和 `timedout`，表示事件。

此函数的行为在不同平台之间略有不同。有关更详细的信息，请参阅 [https://nodejs.org/api/fs.html#fs_caveats](https://nodejs.org/api/fs.html#fs_caveats)。
