```
remoteref_id(r::AbstractRemoteRef) -> RRID
```

`Future`s 和 `RemoteChannel`s 通过以下字段进行标识：

  * `where` - 指的是底层对象/存储实际存在的节点。
  * `whence` - 指的是创建远程引用的节点。请注意，这与底层对象实际存在的节点不同。例如，从主进程调用 `RemoteChannel(2)` 将导致 `where` 值为 2，`whence` 值为 1。
  * `id` 在由 `whence` 指定的工作者创建的所有引用中是唯一的。

综合来看，`whence` 和 `id` 唯一标识了所有工作者中的一个引用。

`remoteref_id` 是一个低级 API，返回一个 `RRID` 对象，该对象封装了远程引用的 `whence` 和 `id` 值。
