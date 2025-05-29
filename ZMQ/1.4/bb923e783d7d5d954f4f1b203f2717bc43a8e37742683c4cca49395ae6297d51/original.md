```
send(socket::Socket, data; more=false)
```

Send `data` over `socket`.  A `more=true` keyword argument can be passed to indicate that `data` is a portion of a larger multipart message. `data` can be any `isbits` type, a `Vector` of `isbits` elements, a `String`, or a [`Message`](@ref) object to perform zero-copy sends of large arrays.
