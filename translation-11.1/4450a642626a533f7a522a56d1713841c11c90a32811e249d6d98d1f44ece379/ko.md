```
read(s::IO, nb=typemax(Int))
```

`s`에서 최대 `nb` 바이트를 읽고, 읽은 바이트의 `Vector{UInt8}`를 반환합니다.
