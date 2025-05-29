```
Message(origin::Any, m::Ptr{T}, len::Integer) where {T}
```

Low-level function to create a message (for send) with an existing data buffer, without making a copy.  The origin parameter should be the Julia object that is the origin of the data, so that we can hold a reference to it until ZMQ is done with the buffer.
