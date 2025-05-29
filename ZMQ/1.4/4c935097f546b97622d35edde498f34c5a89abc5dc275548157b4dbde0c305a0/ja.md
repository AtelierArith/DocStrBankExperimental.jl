```
send(socket::Socket, zmsg::Message; more::Bool=false)
```

ユーザーが割り当てた [`Message`](@ref) を使用した [`Sockets.send(socket, data)`](@ref) のゼロコピー版。
