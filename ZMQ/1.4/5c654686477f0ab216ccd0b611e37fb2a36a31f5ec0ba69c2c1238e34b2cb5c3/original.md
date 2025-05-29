```
mutable struct Message <: AbstractArray{UInt8, 1}
```

High-level `Message` object for sending/receiving ZMQ messages in shared buffers. As an `AbstractArray`, it supports common (non-resizeable) array behaviour.

# Examples

```jldoctest
julia> using ZMQ

julia> m = Message("foo");

julia> Char(m[1])            # Array indexing
'f': ASCII/Unicode U+0066 (category Ll: Letter, lowercase)

julia> m[end] = Int('g');    # Array assignment

julia> unsafe_string(m)      # Conversion to string (only do this if you know the message is a string)
"fog"

julia> IOBuffer(m)           # Create a zero-copy IOBuffer
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=3, maxsize=Inf, ptr=1, mark=-1)
```
