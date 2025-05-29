```
Message(a::T) where T <: DenseVector
```

Create a message with an array as a buffer (for send). Note: the same ownership semantics as for [`Message(m::String)`](@ref) apply.

Usually `a` will be a 1D `Array`/`Vector`, but on Julia 1.11+ it can also be a `Memory`.
