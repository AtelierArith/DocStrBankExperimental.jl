```
recvfrom(socket::UDPSocket) -> (host_port, data)
```

지정된 소켓에서 UDP 패킷을 읽고 `(host_port, data)`의 튜플을 반환합니다. 여기서 `host_port`는 적절하게 `InetAddr{IPv4}` 또는 `InetAddr{IPv6}`가 됩니다.

!!! compat "Julia 1.3"
    Julia 버전 1.3 이전에는 첫 번째 반환 값이 주소(`IPAddr`)였습니다. 버전 1.3에서는 `InetAddr`로 변경되었습니다.

