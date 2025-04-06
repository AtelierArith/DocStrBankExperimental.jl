```
setopt(sock::UDPSocket; multicast_loop=nothing, multicast_ttl=nothing, enable_broadcast=nothing, ttl=nothing)
```

UDP 소켓 옵션을 설정합니다.

  * `multicast_loop`: 멀티캐스트 패킷에 대한 루프백 (기본값: `true`).
  * `multicast_ttl`: 멀티캐스트 패킷에 대한 TTL (기본값: `nothing`).
  * `enable_broadcast`: 소켓이 브로드캐스트 메시지에 사용될 경우 `true`로 설정해야 하며, 그렇지 않으면 UDP 시스템이 접근 오류를 반환합니다 (기본값: `false`).
  * `ttl`: 소켓을 통해 전송되는 패킷의 생존 시간 (기본값: `nothing`).
