```
put!(rr::RemoteChannel, args...)
```

[`RemoteChannel`](@ref)에 값 집합을 저장합니다. 채널이 가득 차면 공간이 생길 때까지 차단됩니다. 첫 번째 인수를 반환합니다.
