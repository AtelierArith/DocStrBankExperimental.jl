```
readbytes!(stream::IOStream, b::AbstractVector{UInt8}, nb=length(b); all::Bool=true)
```

최대 `nb` 바이트를 `stream`에서 `b`로 읽어들이며, 읽은 바이트 수를 반환합니다. 필요할 경우 `b`의 크기가 증가하지만(즉, `nb`가 `length(b)`보다 크고 충분한 바이트를 읽을 수 있는 경우) 감소하지는 않습니다.

`all`이 `true`(기본값)인 경우, 이 함수는 오류나 파일 끝이 발생할 때까지 요청된 모든 바이트를 읽으려고 반복적으로 차단됩니다. `all`이 `false`인 경우, 최대 한 번의 `read` 호출이 수행되며, 반환되는 데이터 양은 장치에 따라 다릅니다. 모든 스트림 유형이 `all` 옵션을 지원하는 것은 아닙니다.
