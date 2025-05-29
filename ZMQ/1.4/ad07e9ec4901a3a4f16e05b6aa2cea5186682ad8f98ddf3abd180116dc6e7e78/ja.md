```
recv(socket::Socket, ::Type{T})
```

型 `T` のメッセージを受信します（通常は `String`、`Vector{UInt8}`、または [`isbits`](https://docs.julialang.org/en/v1/base/base/#Base.isbits) 型）。ZMQ [`Socket`](@ref) から受信します。（メッセージデータのコピーを作成します。大きなメッセージの場合は、ゼロコピーのバイト配列のような表現で作業するために [`recv(socket)`](@ref) を使用することもできます。）
