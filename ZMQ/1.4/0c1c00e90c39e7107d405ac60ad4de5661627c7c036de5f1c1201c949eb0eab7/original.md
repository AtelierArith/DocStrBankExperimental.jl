```
Message(io::IOBuffer)
```

Create a message with an [`IOBuffer`](https://docs.julialang.org/en/v1/base/io-network/#Base.IOBuffer) as a buffer (for send). Note: the same ownership semantics as for [`Message(m::String)`](@ref) apply.
