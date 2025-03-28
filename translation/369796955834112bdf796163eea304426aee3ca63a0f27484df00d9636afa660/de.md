```
channel_from_id(id) -> c
```

Eine Low-Level-API, die das zugrunde liegende `AbstractChannel` für eine `id` zurückgibt, die von [`remoteref_id`](@ref) zurückgegeben wird. Der Aufruf ist nur auf dem Knoten gültig, auf dem der zugrunde liegende Kanal existiert.
