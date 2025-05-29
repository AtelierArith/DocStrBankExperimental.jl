```
send(socket::Socket, zmsg::Message; more::Bool=false)
```

Zero-copy version of [`Sockets.send(socket, data)`](@ref) using a user-allocated [`Message`](@ref).
