```
listen([addr, ]port::Integer; backlog::Integer=BACKLOG_DEFAULT) -> TCPServer
```

지정된 `addr` 주소의 포트에서 수신합니다. 기본적으로 이는 `localhost`에서만 수신합니다. 모든 인터페이스에서 수신하려면 적절하게 `IPv4(0)` 또는 `IPv6(0)`를 전달하십시오. `backlog`는 서버가 연결을 거부하기 시작하기 전에 대기할 수 있는 연결 수( [`accept`](@ref)를 호출하지 않은 상태)를 결정합니다. `backlog`의 기본값은 511입니다.
