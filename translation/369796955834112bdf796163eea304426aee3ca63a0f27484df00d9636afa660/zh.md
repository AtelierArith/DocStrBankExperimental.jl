```
channel_from_id(id) -> c
```

一个低级 API，返回由 [`remoteref_id`](@ref) 返回的 `id` 的后备 `AbstractChannel`。该调用仅在存在后备通道的节点上有效。
