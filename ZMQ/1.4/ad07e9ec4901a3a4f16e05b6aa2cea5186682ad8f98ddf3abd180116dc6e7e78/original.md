```
recv(socket::Socket, ::Type{T})
```

Receive a message of type `T` (typically a `String`, `Vector{UInt8}`, or [`isbits`](https://docs.julialang.org/en/v1/base/base/#Base.isbits) type) from a ZMQ [`Socket`](@ref).  (Makes a copy of the message data; you can alternatively use [`recv(socket)`](@ref) to work with zero-copy bytearray-like representation for large messages.)
