```
readbytes!(stream::IO, b::AbstractVector{UInt8}, nb=length(b))
```

최대 `nb` 바이트를 `stream`에서 `b`로 읽고, 읽은 바이트 수를 반환합니다. 필요할 경우 `b`의 크기가 증가하지만(즉, `nb`가 `length(b)`보다 크고 충분한 바이트를 읽을 수 있는 경우), 절대 감소하지는 않습니다.
