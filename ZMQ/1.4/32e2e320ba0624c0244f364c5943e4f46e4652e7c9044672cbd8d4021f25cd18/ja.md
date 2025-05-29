```
Sockets.bind(socket::Socket, endpoint::AbstractString)
```

ソケットをエンドポイントにバインドします。エンドポイントは[こちら](http://api.zeromq.org/4-3:zmq-bind)に記載されている形式である必要があります。例：`tcp://127.0.0.1:42000`。
